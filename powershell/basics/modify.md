<h1> Data modifications </h1>

[⌂](../../README.md) › [PowerShell](../../README.md#powershell) › [Getting Started](basics.md) ›


Table of Contents
- [Diagnose](#diagnose)
- [Limit data set](#limit-data-set)
- [Properties (columns)](#properties-columns)
- [Sort](#sort)


An understanding of [pipelines](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_pipelines)
is required. 

Everything in PowerShell is already or becomes a .NET object. Therefore, you should be familiar with how to handle and analyze them. Objects are easiest to visualize as text tables, but keep in mind that the entries themselves can also be objects.

- PowerShell modules return objects of a specific type
- external programs return an array of lines `Object[]`  (Array von Textzeilen) zurück.

```powershell
$c = Get-Command
$f = Get-ChildItem
```


# Diagnose

- See object type, properties
	```powershell
	$c | Get-Member -MemberType Properties
	```
	> DIRTY: `| gm`

- Count elements or file lines
	```powershell
	$c.Count
	```


# Limit data set

- **List**:  
  Select the 2nd 4th and 7th item
	```powershell
	$c | select -Index 2, 4, 7 
	```
	```powershell
	$c[@(2;4;7)]
	```
	> DIRTY: `$c[2,4,7]`

- **Range**:  
  Select the first 2 and the last 3 items
	```powershell
	$c | select -First 2 -Last 3
	```
	```powershell
	$c[@(0..1;-3..-1)]
	```
	> DIRTY: `$c[0..1+-3..-1]`

- **Hide duplicates**:  
	If multiple items have equal values, display it only once.
	```powershell
	$c.Noun | select -Unique
	```

- **Condition**  
  Learn operators: `Get-Help about_Comparison_Operators`
	```powershell
	$c | where {$_.Name -match "vpn"}
	```
	> DIRTY: `$c | where Name -match "vpn"`

	``` powershell
	$f | where { `
		( $_.Extension -eq ".xml" -or $_.Name -like "example*" ) `
		-and 
		$_.LastWriteTime -ge [DateTime]::"2000-12-31" `
	}
	```


# Properties (columns)

- View all properties
	```powershell
	$c | select -Property *
	```

- Select properties
	```powershell
	$c | select -Property @("Verb"; "Noun")
	```
	> DIRTY: `$c | select Verb, Noun`

- Add calculated property
	```powershell
	$f | select -Property @(
		"Name";
		@{Label="Size in MB"; Expression={  [Math]::Round($_.Length / 1MB, 2)  }};
	)
	```
	```powershell
	$f | % { Write-Output ([PSCustomObject]@{
		Name = $_.Name;
		"Size in MB" = [Math]::Round($_.Length / 1MB, 2);
  	})}
	```


# Sort

- Sort ascending / default direction
	```powershell
	$c | sort -Property @("Version"; "Name")
	```
	> DIRTY: `$c | sort Version, Name`

- Specify sorting direction
	```powershell
	$c | sort -Property @(
		@{Expression="Version"; Descending=$True};
		"Name";
	)
	```