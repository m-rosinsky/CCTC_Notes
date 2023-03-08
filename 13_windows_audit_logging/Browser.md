# Windows Browser Artifacts

# 1. (5)
Prompt:
```
What Sysinternals tool will allow you to read the SQLite3 database containing the web history of chrome?
```

Answer:
```
strings.exe
```

# 2. (5)
Prompt:
```
Find the questionable website that a user browsed to (using Chrome), that appears to be malicious. *Note: There are more than one users on the box.

Machine: Workstation2 (ssh from Admin_Station)
```

Steps:
```
scp sysinterals

PS C:\Users\student\AppData\Local\Google\Chrome\User Data> C:\SysinternalsSuite\strings.exe .\Default
\History -accepteula | findstr -i https
```

Answer:
```
https://www.exploit-db.com/
```
