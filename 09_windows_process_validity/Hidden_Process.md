# Windows Hidden Processes

# 1. (10)
Prompt:
```
There is malware on the system that is named similarly to a legitimate Windows executable. There is a .dll in the folder that the malware runs from. The flag is the name of the .dll.
```

Steps:
```
Autoruns -> TotallyLegit
```

Answer:
```
libmingwex-0.dll
```

# 2. (10)
Prompt:
```
You notice that there is an annoying pop up happening regularly. Investigate the process causing it. The flag is the name of the executable.
```

Steps:
```
Autoruns -> Look in the Path
```

Answer:
```
McAfeeFireTray.exe
```

# 3. (10)
Prompt:
```
Determine what is sending out a SYN_SENT message. The flag is the name of the executable.

HINT: Use a Sysinternals tool.
```

Steps:
```
TCPView -> syn_sent
```

Answer:
```
McAfeeFireTray.exe
```

# 4. (10)
Prompt:
```
Malware uses names of legit processes to obfuscate itself. Give the flag located in Kerberos’ registry subkey.

HINT: Use Sysinternals tools.

    Creds:
    Machine: Workstation1 (RDP from Admin-Station)
        login: student
        password: password
```

Steps:
```
Autoruns -> Kerberos -> Registry -> Parameters
```

Answer:
```
76aGreX5
```

# 5. (10)
Prompt:
```
There is malware named TotallyLegit. Find its binary location and there will be a file in that directory. Read the file.

HINT: Use Sysinternals tools.
```

Steps:
```
Autoruns -> TotallyLegit

C:\Users\Public\Downloads
```

Answer:
```
GwlkK3sa
```

# 6. (10)
Prompt:
```
Find the McAfeeFireTray.exe. There is a file in that directory. The flag is inside.

HINT: Use Sysinternals tools.

    Creds:
    Machine: Workstation1 (RDP from Admin-Station)
        login: student
        password: password
```

Steps:
```
PS C:\Users\Public\Downloads> cd 'C:\Program Files\Windows Defender Advanced Threat Protection\'                                      PS C:\Program Files\Windows Defender Advanced Threat Protection> ls                                                                                                                                                                                                                                                                                                                                                   Directory: C:\Program Files\Windows Defender Advanced Threat Protection                                                                                                                                                                                                                                                                                                                                       Mode                LastWriteTime         Length Name                                                                                 ----                -------------         ------ ----                                                                                 d-----        4/12/2018   9:21 AM                en-US                                                                                -a----        2/23/2022  10:00 PM              9 It's_Here.txt                                                                        -a----        2/23/2022   9:58 PM         392978 McAfeeFireTray.exe                                                                   -a----        7/15/2018  12:56 AM        4737448 MsSense.exe                                                                          -a----        7/15/2018  12:56 AM         791384 SenseCncProxy.exe                                                                    -a----        7/15/2018  12:43 AM          15360 SenseCncPS.dll                                                                       -a----        7/15/2018  12:56 AM        3832016 SenseIR.exe                                                                          -a----        7/15/2018  12:42 AM         139264 SenseMirror.dll                                                                      -a----        7/15/2018   1:05 AM        2147192 SenseSampleUploader.exe                                                              -a----        4/12/2018   9:20 AM         174592 WATPCSP.dll                                                                                                                                                                                                                                                                                                                                                      PS C:\Program Files\Windows Defender Advanced Threat Protection> cat '.\It''s_Here.txt'                                               StrongBad
```

Answer:
```
StrongBad
```

Answer:
```
GwlkK3sa
```

# 7. (10)
Prompt:
```
A nonstandard port has been opened by possible malware on the system. Identify the port.

    Creds:
    Machine: Workstation1 (RDP from Admin-Station)
        login: student
        password: password
```

Steps:
```powershell
TCPView
```

Answer:
```
6666
```

# 8. (10)
Prompt:
```
Determine what mechanism opened the port from hidden_processes_7. The flag is the name of the file.

Hint: The file is not legit.

    Creds:
    Machine: Workstation1 (RDP from Admin-Station)
        login: student
        password: password
```

Steps:
```powershell
C:\windows\system32>schtasks /query /v /fo list | findstr powershell                                                                             Task To Run:                          powershell.exe -noexit -windowstyle hidden -File C:\windows\system32\legit_script.ps1
```

Answer:
```
legit_script.ps1
```

# 9. (10)
Prompt:
```
Identify the flag from the file in hidden_processes_8.
```

Steps:
```
netstat -ano | findstr 6666 | out-null
if ($lastexitcode -eq 1) {$Listener = [System.Net.Sockets.TcpListener]6666;$Listener.Start();}
# N0t_L3g1T_Ammiright
```

Answer:
```
N0t_L3g1T_Ammiright
```
