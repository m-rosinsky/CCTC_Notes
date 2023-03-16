# Windows Auditing and Logging

Start Key: `start3567`

# 1. Windows Artifacts

andy.dwyer sid: ` S-1-5-21-1204278314-2763755555-735148208-1005`

# 1.1 What is an Artifact?

- Objects or areas within a computer system that contain important information relevant to the activities performed on the system by the user.
- Most artifacts require use of the user SID

```powershell
# Get this SIDs for the users
PS C:\> Get-LocalUser | select Name,SID

# Show domain users as well
PS C:\> Get-WmiObject win32_useraccount | select Name,SID
```

```cmd
C:\>wmic UserAccount get name,sid
```

# 2. UserAssist

- User assist registry key tracks the GUI-based programs run by a user

## 2.1 Location

- `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{GUID}\Count\`
- Encoded in `ROT13`
- GUID represents particular file extension:
    - `CEBFF5CD-ACE2-4F4F-9178-9926F41749EA`: list of applications, files, links
    - `F4E57C4B-2036-45F0-A9AB-443BCFE33D9F`: shortcut links used to start programs

## 2.2 Demos

```powershell
# Show executable files encoded in ROT13
PS C:\> Get-ItemProperty "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{CEBFF5CD-ACE2-4F4F-9178-9926F41749EA}\Count"

# Get shortcut file extention encoded in ROT13
PS C:\> Get-ItemProperty "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{F4E57C4B-2036-45F0-A9AB-443BCFE33D9F}\Count"
```    

- How can we change our command to look at all users Userassist artifacts?

```powershell
PS C:\> Get-ItemProperty "Registry::Hkey_Users\*\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\{CEBFF5CD-ACE2-4F4F-9178-9926F41749EA}\Count"
```

# 3. Windows Background Activity Monitor (BAM)

Show in Reg Edit:
```
# On 1809 and Newer
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\bam\State\UserSettings
```

```
# On 1803 and below
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\bam\UserSettings
```

# 4. Recycle Bin

- Content:
    - SID: The user that deleted it
    - Timestamp: When it was deleted
    - `$RXXXXXX`: Content of deleted files
    - `$IXXXXXX`: Original path and name

```powershell
Get-Childitem 'C:\$RECYCLE.BIN' -Recurse -Verbose -Force | select FullName
```

# 5. Prefetch

- Prefetch entries record the location of the associated executable and files
referenced by that executable.
- Look for any files executed or referenced from a temp directory as this is typically an outlier.

```powershell
Get-Childitem -Path 'C:\Windows\Prefetch' -ErrorAction Continue | select -First 8
```

# 6. Jump Lists

- Task bar allows user to jump to items quickly
- Data stored:
    - First time execution of an application
    - Creation time: First time item added to the AppID file
    - Last time of execution of application w/ file open
    - Modification time

```powershell
Get-Childitem -Recurse C:\Users\*\AppData\Roaming\Microsoft\Windows\Recent -ErrorAction Continue | select FullName, LastAccessTime
```

# 7. Recent Files

```powershell
# Get .txt files
Get-Item 'Registry::\HKEY_USERS\*\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs\.txt'

# Decode
[System.Text.Encoding]::Unicode.GetString((gp "REGISTRY::HKEY_USERS\*\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs\.txt")."0")  
```

# 8. Browser Artifacts
