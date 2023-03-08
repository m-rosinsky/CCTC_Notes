# Windows Last Access

# 1. (5)
Prompt:
```
Figure out the last access time of the hosts file.

Flag format: mm/dd/yyyy
```

Steps:
```powershell
Get-Item C:\Windows\System32\drivers\Etc\hosts | Format-List
```

Answer:
```
02/24/2023
```
