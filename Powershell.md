# PowerShell Notes

Link: https://os.cybbh.io/public/os/latest/index.html

CTFd Address:       `10.50.21.56:8000`

Username:           `MIRO-006-B`

Admin Station IP:   `10.50.33.169`

Stack Number:       `9`

## Cmdlets

#### Write and Read Files
```powershell
Set-Content [filename] [content]
Get-Content [filename]
```

#### PowerShell Variables
```powershell
Get-Variable
```

#### Command Piping
```powershell
# Get processes with id equal to 6968
Get-Process | Select-Object name,id | Where-Object {$_.Id -eq 6968}
```

#### List cmdlets and sort by verb
```powershell
Get-Command -type Cmdlet | Sort-Object -Property verb
```

#### List cmdlets by module
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

## Help
```powershell
Get-Help [command]

Get-Help Get-Process -Examples

# Open docs webpage (NEED GUI)
Get-Help Get-Process -online
```
