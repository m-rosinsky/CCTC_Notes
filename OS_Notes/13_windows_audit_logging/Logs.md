# Windows Logs

# 1. (5)
Prompt:
```
What main Windows log would show invalid login attempts?
```

Answer:
```
Security
```

# 2. (5)
Prompt:
```
What main Windows log will show whether Windows updates were applied recently?
```

Answer:
```
System
```

# 3. (5)
Prompt:
```
When reading logs, you may notice ... at the end of the line where the message is truncated. What format-table switch/argument will display the entire output?

Flag format: -argument
```

Answer:
```
-Wrap
```

# 4. (15)
Prompt:
```
Check event logs for a flag string.

Machine: file-server
```

Steps:
```
PS C:\Users\andy.dwyer> Get-Eventlog -LogName System | ft -wrap | findstr /i flag
                                   cp-Client                         stopped. ShutDown Flag value    
                                   CPv6-Client                       stopped. ShutDown Flag value    
                                   cp-Client                         stopped. ShutDown Flag value    
                                   CPv6-Client                       stopped. ShutDown Flag value    
                                                                     Flag is: 3v3nt_L0g'
                                                                     STILL HAVE NOT found the Flag'  
                                   cp-Client                         stopped. ShutDown Flag value    
                                   CPv6-Client                       stopped. ShutDown Flag value    
                                   cp-Client                         stopped. ShutDown Flag value    
                                   CPv6-Client                       stopped. ShutDown Flag value    
                                   cp-Client                         stopped. ShutDown Flag value    
```

Answer:
```
3v3nt_L0g
```
