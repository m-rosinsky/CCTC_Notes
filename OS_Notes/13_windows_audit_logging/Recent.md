# Windows Recent Files

# 1. (5)
Prompt:
```
What is the registry location of recent docs for the current user?
```

Answer:
```
HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs
```

# 2. (5)
Prompt:
```
There is a file that was recently opened that may contain PII.

Get the flag from the contents of the file.

Hint: We're not interested in numbers.
```

Steps:
```
PS C:\Users\andy.dwyer> Get-Item 'Registry::\HKEY_USERS\*\Software\Microsoft\Windows\CurrentVersion\E
xplorer\RecentDocs\.*'


    Hive: \HKEY_USERS\S-1-5-21-2881336348-3190591231-4063445930-1003\Software\Microsoft\Windows\Curr
    entVersion\Explorer\RecentDocs


Name                           Property
----                           --------
.txt                           6 : {67, 0, 58, 0...}


    Hive: \HKEY_USERS\S-1-5-21-2881336348-3190591231-4063445930-1004\Software\Microsoft\Windows\Curr
    entVersion\Explorer\RecentDocs


Name                           Property
----                           --------
.ps1                           0         : {97, 0, 114, 0...}
                               MRUListEx : {0, 0, 0, 0...}


PS C:\Users\andy.dwyer> [System.Text.Encoding]::Unicode.GetString((gp "REGISTRY::HKEY_USERS\*\SOFTWAR
E\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs\.txt")."6")
C:\Users\student\Documents\3-14-24.txt

PS C:\Users\andy.dwyer> Get-Content C:\Users\student\Documents\3-14-24.txt
Name    SSNPhone Number
Smith, Bob G.   6 6 7 - 2 7 - 3 7 6 7          1 8 6 - 5 2 3 - 9 4 3 7
Washington, Jermaine K.     2 2 7 - 4 4 - 6 6 2 9          8 4 6 - 2 9 7 - 7 4 5 6
Wolf, Winston W.3 8 8 - 6 6 - 3 8 5 6          2 9 5 - 7 6 1 - 1 5 6 8
Prescott, Kelly A.          4 6 5 - 4 9 - 1 3 6 5          4 9 4 - 1 9 7 - 3 4 9 4
Flag, Found A.  1 1 4 - 3 4 - 2 5 4 7          4 8 3 - 5 1 4 - 9 4 3 1
```

Answer:
```
Flag, Found A.
```
