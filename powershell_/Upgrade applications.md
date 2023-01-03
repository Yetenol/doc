# Update all Microsoft Store apps

```powershell
$namespaceName = "root\cimv2\mdm\dmmap"
$className = "MDM_EnterpriseModernAppManagement_AppManagement01"
$wmiObj = Get-WmiObject -Namespace $namespaceName -Class $className
$result = $wmiObj.UpdateScanMethod()
```


# Upgrade all winget apps

```powershell
winget upgrade --all
```

# Update all git repositories

- [shortcutFox-gitUpdateAll.ps1 at main · Yetenol-shortcutFox](https://github.com/Yetenol/shortcutFox/blob/main/source/scripts/gitUpdateAll.ps1)