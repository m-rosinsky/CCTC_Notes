# Windows Services Basics

# 1. (5)
Prompt:
```
What command-line (cmd) command will show service information?
```

Answer:
```
sc
```

# 2. (5)
Prompt:
```
What command-line (cmd) command will show all services, running or not running?

The flag is the full command, for all services.
```

Answer:
```
sc queryex type=service state=all
```

# 3. (5)
Prompt:
```
What PowerShell command will list all services?
```

Answer:
```
Get-Service
```

# 4. (5)
Prompt:
```
What registry location holds all service data?
```

Answer:
```
HKLM\SYSTEM\CurrentControlSet\Services
```

# 5. (5)
Prompt:
```
What registry subkey holds a service's .dll location?

The flag is the subkey name (full path not needed).
```

Answer:
```
Parameters
```

# 6. (10)
Prompt:
```
Services have a name and display name, which could be different. What is the service name of the only Totally-Legit service?
```

Steps:
```powershell
PS C:\> Get-Service | select * | select-string "totally"                                                                                                                                                                                        @{Name=Legit; RequiredServices=System.ServiceProcess.ServiceController[]; CanPauseAndContinue=False;                    CanShutdown=False; CanStop=False; DisplayName=Totally-Legit;                                                            DependentServices=System.ServiceProcess.ServiceController[]; MachineName=.; ServiceName=Legit;                          ServicesDependedOn=System.ServiceProcess.ServiceController[]; ServiceHandle=SafeServiceHandle; Status=Stopped;          ServiceType=Win32OwnProcess; StartType=Automatic; Site=; Container=}
```

Answer:
```
Legit
```

# 7. (10)
Prompt:
```
Figure out the SID of the only Totally-Legit service.

Example: S-1-5-80-159957745-2084983471-2137709666-960844832-[1182961511]

Submit only the [bracketed] portion of the SID.

HINT: Run the command on the service name, not the display name.
```

Steps:
```powershell
andy.dwyer@FILE-SERVER C:\Users\andy.dwyer>sc showsid Legit                                                                                                                                                                                     NAME: Legit                                                                                                             SERVICE SID: S-1-5-80-159957745-2084983471-2137709666-960844832-1182961511                                              STATUS: Inactive 
```

Answer:
```
1182961511
```
