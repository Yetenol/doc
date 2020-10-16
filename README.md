# Powershell cheat sheet
## Export to excel
```
Get-Process | Export-Csv <FILE> -NoType -Delimiter ";"
```

# Tables
## Create table
```
dir | ft Name, Length
```
```
Get-ChildItem | Format-Table -Property Name, Length
```
## Rename table columns
```
Get-ChildItem | Format-Table -Property Name, `
@{Label="Size|Byte"; Expression={$_.Length}}
```
## Custom table columns
```
Get-ChildItem | Format-Table -Property Name, `
@{Label="Size|KB"; Expression={[math]::Round($_.Length / 1KB, 2)}}
```
## Export to excel
```
dir | Export-Csv table.csv -NoType -Delimiter ";"
```
```
Get-ChildItem | Export-Csv -File table.csv -NoTypeInformation -Delimiter ";"
```
## Interesting information
```
Get-ChildItem $env:SystemRoot\* -Include *.exe, *.dll | Format-Table -Property `
BaseName, Extension, `
@{Label="Description"; Expression={[System.Diagnostics.FileVersionInfo]::GetVersionInfo($_).FileDescription}}, `
@{Label="Version"; Expression={[System.Diagnostics.FileVersionInfo]::GetVersionInfo($_).FileVersion}}
```
## Get path apps
```
[String[]]$paths = @($env:path -split ";")
$paths = $paths[0..($paths.Length-2)]
$paths = $paths.ForEach({"$_\*"})
Get-ChildItem -Path $paths -Include *.exe, *.dll `
| Select -Property `
Extension, BaseName, `
@{Label="Description"; Expression={[System.Diagnostics.FileVersionInfo]::GetVersionInfo($_).FileDescription}}, `
@{Label="Version"; Expression={[System.Diagnostics.FileVersionInfo]::GetVersionInfo($_).FileVersion}}, `
@{Label="Size|KB"; Expression={[math]::Round($_.Length / 1KB)}}, `
Directory `
| Sort-Object -Property `
Directory,
@{Expression="Extension"; Descending=$True}, `
@{Expression="Description"; Descending=$False} `
| Export-Csv path-apps.csv -NoType -Delimiter ";"
.\path-apps.csv
```