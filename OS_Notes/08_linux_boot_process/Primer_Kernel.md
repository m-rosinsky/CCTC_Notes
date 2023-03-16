# Primer Kernel

# 1. (1)
Prompt:
```
The Windows NT Operating System attempts to combine features and benefits of microkernel and monolithic kernel architectures, making it which type of kernel architecture?

Research: https://www.educative.io/answers/what-is-windows-kernel
```

Answer:
```
hybrid
```

# 2. (1)
Prompt:
```
The Linux kernel is an example of a this type of kernel architecture?

Research: https://simple.wikipedia.org/wiki/Kernel_(computer_science)
```

Answer:
```
monolithic
```

# 3. (1)
Prompt:
```
Windows operating system name typically differs from its version number. Which Windows version includes Windows 7 and Windows Server 2008R2 and was the 1st version to ship with PowerShell?

**hint - only give the version number

Research: https://learn.microsoft.com/en-us/windows/win32/sysinfo/operating-system-version
```

Answer:
```
6.1
```

# 4. (1)
Prompt:
```
Which Windows version includes Windows Server 2016, 2019, 2022, Windows 10 & 11 and includes SMB 3.1.1 support?

Research: https://learn.microsoft.com/en-us/windows/win32/sysinfo/operating-system-version
```

Answer:
```
10.0
```

# 5. (1)
Prompt:
```
The CMD.EXE tool systeminfo included in Windows is very similar to msinfo32 and displays operating system configuration version information for a local or remote machine, including service pack levels.

Craft a systeminfo command that only returns the below system info: OS Version: "System OS and Build #" BIOS Version: "Your BIOS Ver"

Research: https://ss64.com/nt/systeminfo.html
```

Steps:
```cmd
andy.dwyer@ADMIN-STATION C:\Users\andy.dwyer>systeminfo | find "Version"    
OS Version:                10.0.19045 N/A Build 19045
BIOS Version:              SeaBIOS 1.13.0-1ubuntu1.1, 4/1/2014
```

Answer:
```
systeminfo | find "Version"
```
