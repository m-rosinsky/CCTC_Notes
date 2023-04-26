# Windows Post Exploitation Writeup

Scheme:
```
> jump
-> Pivot: 192.168.28.105
--> T1: 192.168.28.5
```

Pivot:
```
Hostname: ftp.site.donovia
IP: 192.168.28.105
OS: Ubuntu 18.04
Creds: comrade :: StudentReconPassword
Last Known SSH Port: 2222
Malware: none
Action: Perform SSH masquerade and redirect to the next target. No survey required, cohabitation with known PSP approved.
```

T1:
```
Hostname: donovian-windows-private
IP: 192.168.28.5
OS: Windows ver: Unknown
Creds: comrade :: StudentPrivPassword
Last Known Ports: 3389
PSP: unknown
Malware: unknown
Action: Test supplied credentials, if possible gain access to host. Conduct host survey and gain privileged access.
```

##

BthUdTask.exe $(Arg0)

MemoryStatus
C:\MemoryStatus\service.exe
service.exe                   2952 MemoryStatus

hijackmeplz.dll
