# Windows Powershell Profile

Start Flag: `start85678`

## 1. Windows_PowerShell_Profiles1 (5)

Prompt:
```
Which PowerShell profile has the lowest precedence?
```

Answer:
```
Current User, Current Host
```

## 2. Windows_PowerShell_Profiles2 (5)

Prompt:
```
Which PowerShell profile has the highest precedence?
```

Answer:
```
All Users, All Hosts
```

## 3. Windows_PowerShell_Profiles3 (5)

Prompt:
```
Which PowerShell variable stores the current user’s home directory?
```

Answer:
```
$HOME
```

## 4. Windows_PowerShell_Profiles4 (5)

Prompt:
```
Which PowerShell variable stores the installation directory for PowerShell?
```

Answer:
```
$PSHOME
```

## 5. Windows_PowerShell_Profiles5 (5)

Prompt:
```
Which PowerShell variable stores the path to the "Current User, Current Host" profile?
```

Answer:
```
$PROFILE
```

## 6. Windows_PowerShell_Profiles6 (5)

Prompt:
```
What command would you run to view the help for PowerShell Profiles?
```

Answer:
```
Get-Help about_Profiles
```

## 7. Windows_PowerShell_Profiles7 (5)

Prompt:
```
What command would tell you if there was a profile loaded for All Users All Hosts?

Flag is the full command syntax
```

Answer:
```
Test-Path $PROFILE.AllUsersAllHosts
```

## 8. Windows_PowerShell_Profiles8 (10)

Prompt:
```
Challenge only allows ONE attempt

Malware is running in a PowerShell profile on the File-Server. Based on PowerShell profile order of precedence (what is read first), find the correct flag.

The flag is the string after the #, without the preceding space.
```

Steps:
```powershell
Get-Content $PROFILE.AllUsersAllHosts
```

Answer:
```
I am definitely not the malware
```
