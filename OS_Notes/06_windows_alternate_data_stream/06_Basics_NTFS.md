## 1. Windows File System Basics 1 (5)

Prompt:
```
Every file on a Windows system has attributes. What does the d attribute mean?
```

Answer:
```
directory
```

## 2. Windows File System Basics 2 (5)

Prompt:
```
Every file on a Windows system has attributes. What does the h attribute mean?
```

Answer:
```
hidden
```

## 3. Windows File System Basics 3 (5)

Prompt:
```
What PowerShell command will list all files in the current directory, regardless of their attributes?
```

Answer:
```
Get-ChildItem -Force
```

## 4. Windows File System Basics 4 (5)

Prompt:
```
What PowerShell command will give you the sha512 hash of a file?

Flag format: PS-command -argument
```

Answer:
```
Get-FileHash -Algorithm Sha512
```

## 5. Windows File System Basics 5 (5)

Prompt:
```
What PowerShell command will list permissions of a file?
```

Answer:
```
Get-Acl
```

## 6. Windows File System Basics 6 (5)

Prompt:
```
What Windows file maps hostnames to IP addresses?
```

Answer:
```
C:\Windows\System32\Drivers\etc\hosts
```

## 7. Windows File System Basics 7 (10)

Prompt:
```
Which group has ReadandExecute (RX) permissions to the file listed in the previous challenge, File_System_Basics_6?
```

Steps:
```powershell
Get-Acl C:\Windows\System32\Drivers\etc\hosts | Format-Table -Wrap
```

Answer:
```
BUILTIN\Users
```

## 8. Windows File System Basics 8 (10)

Prompt:
```
Find the last five characters of the MD5 hash of the hosts file.
```

Steps:
```powershell
Get-FileHash C:\Windows\System32\Drivers\etc\hosts -Algorithm md5
```

Answer:
```
7566D
```

## 9. Windows File System Basics 9 (10)

Prompt:
```
Examine the readme file somewhere in the CTF user’s home directory.
```

Steps:
```powershell
PS C:\Users\CTF> Get-ChildItem -recurse -Include readme    


    Directory: C:\Users\CTF\Favorites


Mode                LastWriteTime         Length Name      
----                -------------         ------ ----      
-a----        2/23/2022   9:56 PM             18 README    


PS C:\Users\CTF> Get-Content C:\Users\CTF\Favorites\README
123456
```

Answer:
```
123456
```

## 10. Windows File System Basics 10 (10)

Prompt:
```
There is a hidden directory in the CTF user's home directory. The directory contains a file. Read the file.
```

Steps:
```powershell
PS C:\Users\CTF> ls -Hidden


    Directory: C:\Users\CTF


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d--h--        2/23/2022   9:56 PM                secretsauce


PS C:\Users\CTF> ls .\secretsauce\


    Directory: C:\Users\CTF\secretsauce


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/23/2022   9:56 PM             20 saucey


PS C:\Users\CTF> Get-Content .\secretsauce\saucey
ketchup
```

Answer:
```
ketchup
```

## 11. Windows File System Basics 11 (10)

Prompt:
```
Find a file in a directory on the desktop with spaces in it. FLAG is the contents of the file

HINT: If you like to type the full names and paths of files, you better look for a shortcut.
```

Steps:
```powershell
PS C:\Users\CTF\Desktop> Get-Content '.\z                                                                                                             -
              a\spaces.txt'
987654321
```

Answer:
```
987654321
```

## 12. Windows File System Basics 12 (10)

Prompt:
```
Find the Alternate Data Stream in the CTF user's home, and read it.
```

Steps:
```powershell
# List all alt streams.
gci -recurse | % { gi $_.FullName -stream * } | where stream -ne ':$Data'

# Read the alt stream of the file.
Get-Content -Stream hidden .\Documents\nothing_here   
```

Answer:
```
P455W0RD
```

## 13. Windows File System Basics 13 (10)

Prompt:
```
"Fortune cookies" have been left around the system so that you won't find the hidden password...
```

Steps:
```powershell
PS C:\> gci -recurse | % { gi $_.FullName -stream * } | where stream -ne ':$Data'

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Windows\PLA\not_anihc\The Fortune Cookie:none
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Windows\PLA\not_anihc
PSChildName   : The Fortune Cookie:none
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Windows\PLA\not_anihc\The Fortune Cookie
Stream        : none
Length        : 26

PS C:\> Get-Content -Stream none 'C:\Windows\PLA\not_anihc\The Fortune Cookie'
```

Answer:
```
fortune_cookie
```

## 14. Windows File System Basics 14 (10)

Prompt:
```
There are plenty of phish in the C:\, but sometimes they're hidden in plain site.

Find the phish.
```

Steps:
```powershell
ls -hidden -recurse | Get-Content
```

Answer:
```
phi5hy
```
