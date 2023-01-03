#obsidian/translate #powershell/test

The data is encrypted using the Windows Data Protection API (DPAPI). 
Only the **SAME USER ON THE SAME MASHINE** can decrypt.

# Eingabe eines sicheren Texts

1. Consoleneingabe
    ```powershell
    Read-Host "Password" -AsSecureString # secure string
    ```
1. Credential erzeugen
    ```powershell
    Get-Credential | ConvertTo-SecureString -AsPlainText -Force # secure string
    ```

1. Klartextkonvertierung
	```powershell
	| ConvertTo-SecureString -AsPlainText -Force
	```
1. Importieren verschlüsselter Datei
	```powershell
    Get-Content -Path ".\secure.bin" `
    | ConvertTo-SecureString
    ```

# Dateispeicherung

1. XML-Objekt verschlüsselt speichern
    ```powershell
    | Export-Clixml ".\temp.xml"

    $xml = Get-Content -Path ".\temp.xml" -Raw
    ConvertTo-SecureString -AsPlainText $xml -Force `
    | ConvertFrom-SecureString `
    | Out-File secure.bin

    Remove-Item -Path ".\temp.xml"
    ```
1. Verschlüsseltes XML-Objekt importieren
    ```powershell
    $secure = Get-Content -Path ".\secure.bin" `
    | ConvertTo-SecureString

    $bstr = [Runtime.InteropServices.Marshal]::SecureStringToBSTR($secure)
	$xml = [Runtime.InteropServices.Marshal]::PtrToStringAuto($bstr)
    $xml | Out-File ".\temp.xml"
    $object = Import-Clixml ".\temp.xml"
    Remove-Item -Path ".\temp.xml"
    $object
    ```

    ```
	| ConvertTo-SecureString -AsPlainText -Force `
	| ConvertFrom-SecureString `
	| Out-File -FilePath ".\key.bin"
	```


1. Sicherer Text -> Klartext
    ```powershell
    $secure = Get-Item <# #>
	$bstr = [Runtime.InteropServices.Marshal]::SecureStringToBSTR($secure)
	$plaintext = [Runtime.InteropServices.Marshal]::PtrToStringAuto($bstr)
	$plaintext
    ```

## Import from file

Only the <b>SAME USER ON THE SAME MASHINE</b> can decrypt.

```powershell
$Secure = Get-Content "${Env:AppData}\Sec.bin" | ConvertTo-SecureString
```


---
Sources:

Related:
[Sensitive input](Sensitive%20input.md)

Tags: