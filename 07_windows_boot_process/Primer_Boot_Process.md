# Primer Atom Boot Process

# 1. (1)
Prompt:
```
What is the smallest addressable unit on a hard disk?

Research: https://learn.microsoft.com/en-us/windows/win32/fileio/disk-devices-and-partitions
```

Answer:
```
sector
```

# 2. (1)
Prompt:
```
What term describes a logical division of a single storage device?

Research: https://learn.microsoft.com/en-us/windows/win32/fileio/disk-devices-and-partitions
```

Answer:
```
partition
```

# 3. (1)
Prompt:
```
What term describes a formatted storage device that can span 1 or more partitions, has a single file system and is assigned a drive letter?

Research: https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/storage-device-stacks--storage-volumes--and-file-system-stacks
```

Answer:
```
volume
```

# 4. (1)
Prompt:
```
What CLI disk partitioning tool is available in Windows to view and manipulate both partitions and volumes?

Research: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/diskpart
```

Answer:
```
diskpart
```

# 5. (1)
Prompt:
```
Windows includes 4 critical Kernel-mode components. Which component is a matched pair with the kernel and obfuscates the hardware dependencies from the kernel?
```

Answer:
```
HAL
```

# 6. (1)
Prompt:
```
Windows includes 4 critical Kernel-mode components. Which component directs calls from a user-mode process to the kernel services?
```

Answer:
```
Executive
```

# 7. (1)
Prompt:
```
This provides an operating system with a software interface to a hardware device

Research: https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/what-is-a-driver-
```

Answer:
```
driver
```

# 8. (1)
Prompt:
```
What are the two firmware interfaces supported by modern computers and read in the Pre-boot phase of the Windows boot process?

**Hint, answer format = _______ and _______

Research: https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/boot-to-uefi-mode-or-legacy-bios-mode?view=windows-11
```

Answer:
```
BIOS and UEFI
```

# 9. (1)
Prompt:
```
What is the name of the process that spawns SYSTEM?

Research: https://en.wikipedia.org/wiki/Windows_NT_booting_process (Hint: What really is SYSTEM?)
```

Answer:
```
Ntoskrnl.exe
```

# 10. (1)
Prompt:
```
In Windows what does the boot sector code load into memory?

**Hint - Flag Format = ________ and ________

(Hint: What two things are between the MBR and the Kernel?) Research: https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/windows-boot-issues-troubleshooting
```

Answer:
```
bootmgr and winload
```

# 11. (1)
Prompt:
```
In Windows 10 what is the name of the boot manager?

Research: https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/windows-boot-issues-troubleshooting
```

Answer:
```
bootmgr
```

# 12. (1)
Prompt:
```
In Microsoft Vista and later the boot.ini file was replaced by what?

Research: https://learn.microsoft.com/en-us/windows-hardware/drivers/devtest/boot-options-in-windows
```

Answer:
```
bcd
```

# 13. (1)
Prompt:
```
What is the tamper-resistant processor mounted on the motherboard used to improve the security of your PC. It's used by services like BitLocker drive encryption and Windows Hello to securely create and store cryptographic keys, and to confirm that the operating system and firmware on your device are what they're supposed to be, and haven't been tampered with.

Research: https://learn.microsoft.com/en-us/windows/security/information-protection/tpm/tpm-fundamentals
```

Answer:
```
tpm
```

# 14. (1)
Prompt:
```
During the Windows boot process, what starts BOOT_START device drivers and services with value of 0x0 in the registry key HKLM\SYSTEM\CurrentControlSet\Services?

Research: https://www.lifewire.com/what-is-winload-exe-2626051
```

Answer:
```
winload
```

# 15. (1)
Prompt:
```
During the Windows boot process, what starts SYSTEM_START device drivers and services with hex value of 0x1 in the registry key HKLM\SYSTEM\CurrentControlSet\Services?

Research: https://en.wikipedia.org/wiki/Ntoskrnl.exe
```

Answer:
```
ntoskrnl
```

# 16. (1)
Prompt:
```
During the Windows boot process, services.exe starts device drivers and services on demand with what hex value in the registry key HKLM\SYSTEM\CurrentControlSet\Services?

    hint syntax - #x#

Research: https://winreg-kb.readthedocs.io/en/latest/sources/system-keys/Services-and-drivers.html
```

Answer:
```
0x3
```

# 17. (1)
Prompt:
```
Starting in Windows Vista, what process spawns two additional instances (with identical names), used to initiate session 0 and session 1?

Research: https://www.ghacks.net/2007/12/27/csrssexe-smssexe-and-lsassexe/
https://techcommunity.microsoft.com/t5/ask-the-performance-team/sessions-desktops-and-windows-stations/ba-p/372473
```

Answer:
```
smss
```

# 18. (1)
Prompt:
```
Which Windows Vista user session is non-interactive, contains system services and processes and is isolated from the GDI (Graphical Device Interface)

Research: https://techcommunity.microsoft.com/t5/ask-the-performance-team/sessions-desktops-and-windows-stations/ba-p/372473
```

Answer:
```
0
```

# 19. (1)
Prompt:
```
What is the boot process security feature available in UEFI systems, that only allows verified drivers to load?

Research: https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-secure-boot
```

Answer:
```
secure boot
```

# 20. (1)
Prompt:
```
To make booting faster, starting with Windows 8, the OS does a partial ________ of the kernel session at shutdown?

Research: https://learn.microsoft.com/en-us/windows/win32/power/system-power-states
```

Answer:
```
hibernate
```

# 21. (1)
Prompt:
```
What registry key is responsible for starting services on your machine during the boot process? Flag is the full registry path.

Research: https://www.picussecurity.com/resource/blog/picus-10-critical-mitre-attck-techniques-t1060-registry-run-keys-startup-folder
```

Answer:
```
hibernate
```
