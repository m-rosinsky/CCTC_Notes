```
Get-Item registry::hkey_users\{sid}\Microsoft\Windows\CurrentVersion
```

## 1. Windows_Registry_Basics1 (5)
Prompt:
```
What registry hive contains all machine settings?
```

Answer:
```
HKEY_LOCAL_MACHINE
```

## 2. Windows_Registry_Basics2 (5)
Prompt:
```
What registry hive contains all user settings?
```

Answer:
```
HKEY_USERS
```

## 3. Windows_Registry_Basics3 (5)
Prompt:
```
What registry hive contains only the currently logged-in user's settings?
```

Answer:
```
HKEY_CURRENT_USER
```

## 4. Windows_Registry_Basics4 (5)
Prompt:
```
The HKEY_CURRENT_USER registry hive is a symbolic link to another registry subkey. What is the subkey that it is linked to?

Flag format: HIVE\SID.........................
```

Answer:
```
HKEY_USERS\S-1-5-21-1204278314-2763755555-735148208-1005
```

## 5. Windows_Registry_Basics5 (5)
Prompt:
```
What PowerShell command will list all the subkeys and contents in the current directory and/or will list all the subkeys and the contents of a directory you specify?
```

Answer:
```
Get-ChildItem
```

## 6. Windows_Registry_Basics6 (5)
Prompt:
```
What PowerShell command will list only the contents of a registry key or subkey?
```

Answer:
```
Get-Item
```

## 7. Windows_Registry_Basics7 (10)
Prompt:
```
What registry subkey runs every time the machine reboots? The flag is the full path, using PowerShell.

Flag format: FULL\PATH\ALL\CAPS
```

Answer:
```
HKLM\SOFTWARE\MICROSOFT\WINDOWS\CURRENTVERSION\RUN
```

## 8. Windows_Registry_Basics8 (10)
Prompt:
```
What registry subkey runs every time a user logs on? The flag is the full path, using PowerShell.

Flag format: FULL\PATH\ALL\CAPS
```

Answer:
```
HKLM\SOFTWARE\MICROSOFT\WINDOWS\CURRENTVERSION\RUN
```

## 9. Windows_Registry_Basics9 (10)
Prompt:
```
What registry subkey runs a single time, then deletes its value once the machine reboots? The flag is the full path, using PowerShell.

Flag format: FULL\PATH\ALL\CAPS
```

Answer:
```
HKLM\SOFTWARE\MICROSOFT\WINDOWS\CURRENTVERSION\RUNONCE
```

## 10. Windows_Registry_Basics10 (10)
Prompt:
```
What registry subkey runs a single time, then deletes its value when a user logs on? The flag is the full path, using PowerShell.

Flag format: FULL\PATH\ALL\CAPS
```

Answer:
```
HKEY_CURRENT_USER\SOFTWARE\MICROSOFT\WINDOWS\CURRENTVERSION\RUNONCE
```

## 11. Windows_Registry_Basics11 (15)
Prompt:
```
What is the value inside of the registry subkey from your previous challenge named registry_basics_7?
```

Steps:
```powershell
Get-Item HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```

Answer:
```
C:\malware.exe
```

## 12. Windows_Registry_Basics12 (15)
Prompt:
```
What is the value inside of the registry subkey that loads every time the "Student" user logs on?
```

Steps:
```powershell
# Get username | sid matches
Get-LocalUser | select name,sid

Get-Item registry::HKEY_USERS\S-1-5-21-2881336348-3190591231-4063445930-1003
\Software\Microsoft\Windows\CurrentVersion\Run
```

Answer:
```
C:\botnet.exe
```

## 13. Windows_Registry_Basics13 (15)
Prompt:
```
What is the value inside of the registry subkey from registry_basics_9?
```

Steps:
```powershell
Get-Item HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce
```

Answer:
```
C:\virus.exe
```

## 14. Windows_Registry_Basics14 (15)
Prompt:
```
What is the value inside of the registry subkey that loads a single time when the "student" user logs on?
```

Steps:
```powershell
Get-Item registry::HKEY_USERS\S-1-5-21-2881336348-3190591231-4063445930-1003\Software\Microsoft\Windows\CurrentVersion\RunOnce
```

Answer:
```
C:\worm.exe
```

## 15. Windows_Registry_Basics15 (15)
Prompt:
```
Figure out the manufacturer's name of the only USB drive that was plugged into this machine.
```

Steps:
```powershell
Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Enum\USBSTOR
```

Answer:
```
SanDisk9834
```

## 16. Windows_Registry_Basics16 (15)
Prompt:
```
What suspicious user profile, found in the registry, has connected to this machine?
```

Steps:
```powershell
Get-ChildItem "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList\"
```

Answer:
```
Hacker McHackerson
```

## 17. Windows_Registry_Basics17 (15)
Prompt:
```
What suspicious wireless network, found in the registry, has this system connected to?
```

Steps:
```powershell
Get-ChildItem "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Profiles"
```

Answer:
```
Terror_cafe_network
```
