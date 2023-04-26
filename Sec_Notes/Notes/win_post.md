# Windows Post Exploitation

Scheduled Tasks:
```
schtasks /query /fo LIST /v | Select-String -Pattern "Task to Run"| find /i /v "com handler"
```

Query Session:
```
tasklist /v
query session
```

WMIC Process:
```
wmic process get name,processid,parentprocessid,sessionid
wmic process where (processid=id) list full
tasklist /svc | findstr /i "id"
where /R c:\ putty
```

ICACLS:
```
icacls [path]
```

DLL Hijacking:
```

```

Finding Vulnerable Services:

1. services.msc
2. Description Sort
    - All default windows services have descriptions
3. Properties to see exec path
4. For loop to find things not running in `system32`
5. Find autostart services
```

```cmd
sc qc [service name]
icacls [executable]
Rename actual exec to another name.
Rename bad exec to actual exec.
Reboot.
```

## Triage:

Check Registry:

- Run
- RunOnce

## AuditPol

```
auditpol /get /category:*
auditpol /get /category:* | findstr /i "success failure"
```

Important Event IDs:

- 4624/5625 -> Success / failed login
- 4720 -> Account created
- 4672 -> Admin logged in
- 7045

wevtutil
```
wevtutil qe system /c:10 /rd:true /f:text
```

Import Logs:

1. Open Event Viewer
2. Open Saved Log...
3. Select it.
