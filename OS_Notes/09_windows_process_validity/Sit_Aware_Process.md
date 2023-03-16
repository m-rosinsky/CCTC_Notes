# Windows Process Situational Awareness

# 1. (10)
Prompt:
```
What are the permissions for NT SERVICE\TrustedInstaller on spoolsv.exe? Copy the permissions from your shell.

HINT: Use Sysinternals tools.
```

Steps:
```powershell
Get-ChildItem -Recurse "C:\" -Name spoolsv.exe

.\accesschk.exe <path>
```

Answer:
```
RW
```

# 2. (10)
Prompt:
```
What is the PATH listed in the output when we find the handle for spoolsv.exe?

HINT: Use Sysinternals tools and don't forget to run as Administrator...
```

Steps:
```powershell
PS C:\Users\student> .\Desktop\Sysinternals\handle.exe | findstr "spoolsv.exe"                                                        spoolsv.exe pid: 2344 NT AUTHORITY\SYSTEM                                                                                                90: File  (R-D)   C:\Windows\System32\en-US\spoolsv.exe.mui
```

Answer:
```
C:\Windows\System32\en-US\spoolsv.exe.mui
```

# 3. (10)
Prompt:
```
In what Load Order Group is the Windows Firewall service?

HINT: Use Sysinternals tools.
```

Steps:
```powershell
PS C:\Users\student\Desktop\Sysinternals> .\LoadOrdC.exe | findstr "mpssvc"                                                           Automatic    NetworkProvider           n/a*       mpssvc                         @%SystemRoot%\system32\FirewallAPI.dll,-23090      %SystemRoot%\system32\svchost.exe -k LocalServiceNoNetwork -p
```

Answer:
```
NetworkProvider
```

# 4. (10)
Prompt:
```
What is the first .dll associated with winlogon.exe? Provide the name of the .dll only, not the /absolute/path

HINT: Use Sysinternals tools.
```

Steps:
```powershell
tasklist /, | more
```

Answer:
```
ntdll.dll
```

# 5. (10)
Prompt:
```
While examining the Windows Defender Firewall, what is the LogAllowedConnections setting set to, for the Public profile?
```

Steps:
```powershell
netsh advfirewall show allprofiles

Public Profile Settings:
---------------------------------------------------------------------
LogAllowedConnections Disable                                                                           
```

Answer:
```
Disable
```

# 6. (10)
Prompt:
```
While examining the Windows Defender Firewall, what is the LogAllowedConnections setting set to, for the Public profile?
```

Steps:
```powershell
netsh advfirewall show allprofiles

Public Profile Settings:
---------------------------------------------------------------------
LogAllowedConnections Disable                                                                           
```

Answer:
```
Disable
```
