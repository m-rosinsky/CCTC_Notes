# Windows Auditing and Logging

Start Key: `start`

# 1. Windows Artifacts

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
