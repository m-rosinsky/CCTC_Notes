# Primer Networking

# 1. (1)
Prompt:
```
What is used in Windows to implement the networking stack to enable communication with the four lowest OSI layers?
```

Answer:
```
NDIS
```

# 2. (1)
Prompt:
```
What Windows cmd.exe command will display the local coputer's routing table?
```

Answer:
```
netstat
```

# 3. (1)
Prompt:
```
IANA assigned TCP/UDP ports in the range of 0-1023 that are usually associated with server-side services are known as?
```

Answer:
```
well known
```

# 4. (1)
Prompt:
```
What term describes randomly assigned TCP/UDP ports above 1023 and are used for a short period of time (for the duration of a communication session}?
```

Answer:
```
ephemeral
```

# 5. (1)
Prompt:
```
The two words that decribe translating Host names to IP addresses or NetBIOS names to IP addresses is_____?
```

Answer:
```
name resolution
```

# 6. (1)
Prompt:
```
What is the hierarchical service/protocol that translates hostnames to IP addresses?
```

Answer:
```
dns
```

# 7. (1)
Prompt:
```
What CLI tool is often used to troubleshoot DNS issues but can also be used in reconnaissance?
```

Answer:
```
nslookup
```

# 8. (1)
Prompt:
```
In Windows 10 what is the full path to the hosts file? Complete the path c:\Windows____________
```

Answer:
```
\System32\drivers\etc\hosts
```

# 9. (1)
Prompt:
```
Fill in the missing component for the usual Host Name Resolution order:

    Client checks own host name
    Client searches local Hosts file
    ______________________
    NetBIOS name resolution sequence is used as a backup

Flag Format: Full name or acronym
```

Answer:
```
dns
```

# 10. (1)
Prompt:
```
What cmd.exe tool will display NetBIOS transport statistics in Windows?
```

Answer:
```
nbtstat
```

# Security

# 1. (1)
Prompt:
```
What is the term for the numeric value that the Windows OS uses to uniquely ID a user, group or computer?
```

Answer:
```
sid
```

# 2. (1)
Prompt:
```
What switch can be added to the CMD.exe command whoami, to view the SID of the current user?
```

Answer:
```
/user
```

# 3. (1)
Prompt:
```
What is the value of a Relative Identifier (RID) assigned to the 1st user account?
```

Answer:
```
1000
```

# 4. (1)
Prompt:
```
What is the well known RID for the Windows Built-In Administrator Local account?
```

Answer:
```
500
```

# 5. (1)
Prompt:
```
Complete the GET_CimInstance cmdlet to view all the user SIDs on a Windows host machine by Name and SID respectively:

Get-CimInstance Win32_UserAccount | Select-Obect ______________

**hint: the output will ONLY include Name and SID
```

Answer:
```
name,sid
```

# 6. (1)
Prompt:
```
In Windows what else does a user's security Token contain?

    SIDS of groups of which the user is a member
    Privilege array
    The Users _________ ?

**hint: Flag describes the unique number assigned to the user
```

Answer:
```
sid
```

# 7. (1)
Prompt:
```
When contained in a Windows users access token, what privilege does SeBackupPrivilege grant to the user to perform on files and folders?

**hint - flag is one word
```

Answer:
```

```

# 8. (1)
Prompt:
```
Windows performs mandatory integrity checks (MICs) by comparing the integrity level of the resource with the integrity level of the calling process. Windows does this integrity check before the the objects discretionary access check because it is _____________?
```

Answer:
```
faster
```

# 9. (1)
Prompt:
```
A Windows object's Security _________ contains:

    The SID of the object's owner
    Discretionary Access Control List (DACL)
    System Access Control List (SACL)
```

Answer:
```
descriptor
```

# 10. (1)
Prompt:
```
What contains Access Control Entries (ACEs), that define the types of access a user or group may be granted to an object?
```

Answer:
```
DACL
```

# 11. (1)
Prompt:
```
What cmdlet gets objects that represent the security descriptor of a file or resource?
```

Answer:
```
get-acl
```

# 12. (1)
Prompt:
```
What NET cmd.exe command can be used to enumerate the local Windows group accounts?
```

Answer:
```
net localgroup
```

# 13. (1)
Prompt:
```
What Windows cmd.exe command will display or modify Access Control Lists (ACLs) for files and folders and resolves various issues that occur when using the older CACLS & XCACLS.
```

Answer:
```
icacls
```

# 14. (1)
Prompt:
```
What Windows security feature is a system-level memory protection feature that is built into the operating system starting with Windows XP and Windows Server 2003 and enables the system to mark one or more pages of memory as non-executable?
```

Answer:
```
data execution prevention
```

# 15. (1)
Prompt:
```
What computer security technique is used in Windows to prevent exploitation of memory corruption vulnerabilities? This feature randomly arranges the address space positions of key data areas of a process, in order to prevent an attacker from reliably jumping to, a particular exploited function in memory.
```

Answer:
```
address space layout randomization
```

# 16. (1)
Prompt:
```
What is a small kernel-mode library that can implement API hooking?
```

Answer:
```
shim
```

# 17. (1)
Prompt:
```
Which security feature helps keep attackers from gaining access through Pass-the-Hash or Pass-the-Ticket attacks useing virtualization-based security to isolate secrets, such as NTLM password hashes and Kerberos Ticket Granting Tickets?
```

Answer:
```
credential guard
```

# 18. (1)
Prompt:
```
Introduced in Windows 8 this is Microsoft Antivirus, anti-malware solution?
```

Answer:
```
windows defender
```

# 19. (1)
Prompt:
```
What security technique helps prevent overwrites of the Structured Exception Handler?
```

Answer:
```
sehop
```

# 20. (1)
Prompt:
```
What security protection is built into Windows 10, as described in the "Memory reservations" item in Kernel pool protections? This includes protecting address space 0x00000000 (not listed in article).
```

Answer:
```
NULL
```

# 21. (1)
Prompt:
```
What security protection is built into Windows 10, as described in the "Memory reservations" item in What Windows security feature prevents the replacement of essential system files, folders, and registry keys that are installed as part of the operating system? It became available starting with Windows Server 2008 and Windows Vista.
```

Answer:
```
wrp
```

# 22. (1)
Prompt:
```
What option should you use with the System File Checker cmd.exe tool sfc.exe to scan all protected system files, and replace corrupted files with a cached copy that is located in a compressed folder at %WinDir%\System32\dllcache ?
```

Answer:
```
/scannow
```

# 23. (1)
Prompt:
```
Where are copies of known-good critical system files located at %WinDir%___________ and used by the Windows Resource Protection feature?
```

Answer:
```
\winsxs\backup
```

# Surveys

# 1. (1)
Prompt:
```
What team survey is focused on security and auditing?
```

Answer:
```
red
```

# 2. (1)
Prompt:
```
What type of survey is focused on computer system settings, updates, configurations and installed software?
```

Answer:
```
blue
```

# 3. (1)
Prompt:
```
What type of survey is focused on malware detection, artifact detection and investigating processes?
```

Answer:
```
incident response
```
