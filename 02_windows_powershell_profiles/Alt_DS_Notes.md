# Alternate Data Streams Notes

## Data Streams in Command Prompt

#### Creating a regular data stream on a file
```cmd
C:\windows\system32>echo Always try your best > reminder.txt

C:\windows\system32>dir reminder.txt
 Directory of C:\windows\system32
 02/27/2021 07:13 PM                 25 reminder.txt
                1 File(s)            25 bytes
                0 Dir(s) 20,060,768,688 bytes free

C:\windows\system32>type reminder.txt
Always try your best
```

#### Creating an Alternate Data Stream on a file
```cmd
C:\windows\system32>echo social security numbers > reminder.txt:secret.info

C:\windows\system32>dir reminder.txt
 Directory of C:\windows\system32
 02/27/2021 07:13 PM                  23 reminder.txt
                 1 File(s)            23 bytes
                 0 Dir(s) 20,060,712,960 bytes free

C:\windows\system32>type reminder.txt
Always try your best

C:\windows\system32>more < rem.txt:secret.info
social security numbers
```

## Data Streams in PowerShell

#### Creating regular data stream on a file.
```powershell
PS C:\> echo "normal stuff" > rem.txt

PS C:\?Get-Content rem.txt
normal stuff

PS C:\> Set-Content .\rem.txt -Value "secret stuff" -Stream secret.info

# List all streams.
PS C:\> Get-Item .\rem.txt -Stream *


PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\rem.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\
PSChildName   : rem.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\rem.txt
Stream        : :$DATA
Length        : 30

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\rem.txt:secret.info
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\
PSChildName   : rem.txt:secret.info
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\rem.txt
Stream        : secret.info
Length        : 14

PS C:\> Get-Item .\rem.txt -Stream * | select FileName, Stream

FileName   Stream
--------   ------
C:\rem.txt :$DATA
C:\rem.txt secret.info

PS C:\> Get-Content .\rem.txt -Stream secret.info
secret stuff
```
