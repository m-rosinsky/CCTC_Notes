# Primer Auditing

# 1. (1)
Prompt:
```
Logging, Auditing and Monitoring are often confused with each other but are distinctly different. Which term refers to real-time analysis and is often accomplished with a Security Event Information Management system (SIEM)?
```

Answer:
```
Monitoring
```

# 2. (1)
Prompt:
```
What term is most appropriate when referring to the process of reviewing log files or other records for specified period?
```

Answer:
```
Auditing
```

# 3. (1)
Prompt:
```
"Complete the following path to the Windows System Log which records system events e.g. startup and shutdown: %systemroom%\System32_______________
```

Answer:
```
\WinEvt\Logs\System.evtx
```

# 4. (1)
Prompt:
```
Which Windows log contains either success or failures and can be configured to record failed logon attempts?
```

Answer:
```
security
```

# 5. (1)
Prompt:
```
"Which Windows account is the only account to have WRITE-APPEND access to Windows event logs?"

Resource: https://os.cybbh.io/public/os/latest/011_windows_auditing_&_logging/primer.html#_7_describe_the_systems_audit_policy
```

Answer:
```
system
```

# 6. (1)
Prompt:
```
What is parsed in an NTFS object's security descriptor, by the Security Reference Monitor (SRM), to determine if an audit entry will be created in the Windows Security Log?

Research: https://learn.microsoft.com/en-us/windows/win32/secauthz/access-control-lists
```

Answer:
```
SACL
```

# 7. (1)
Prompt:
```
Which registry key holds the audit policy configuration? **Hint - Give full path
```

Answer:
```
HKLM\Security\Policy\PolAdtEv
```

# 8. (1)
Prompt:
```
Which sysinternals tool is used to parse logs?
```

Answer:
```
PsLogList
```
