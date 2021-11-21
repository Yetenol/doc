# Bluetooth

### List all bluetooth devices
```powershell
Get-PnpDevice -Class Bluetooth | where HardwareID -Match "\\DEV_"
```