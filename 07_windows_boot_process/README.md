# Windows Boot Process

Start Key: `start`

## BIOS and UEFI

Windows Boot Process
| ![alt text](http://1.bp.blogspot.com/-MaRtDTHH1Vo/UysJF8KXNbI/AAAAAAAAALo/D6Kt2f8Gpmo/s1600/Walkthrough_Diagram.jpg "Windows Boot Process") |
|:--:|

1. Hardware Init.
2. Load boot sector or boot manager.
3. Loading the OS from the boot sector.

| ![alt text](https://git.cybbh.space/os/public/raw/master/images/BIOSvsUEFI.png "Windows Boot Process") |
|:--:|

#### Security in Boot

- Rootkits can hide themselves in the boot process.
- Bootkits replace the OS bootloader to load the bootkit before the OS.

## BIOS Checking

```powershell
PS C:\Users\andy.dwyer> Get-Content C:\Windows\Panther\Setupact.log | Select-String "Detected boot environment"

2022-12-30 19:38:33, Info                  IBS    Callback_BootEnvironmentDetect: Detected boot
environment: BIOS
```

```powershell
PS C:\Users\andy.dwyer> bcdedit | findstr /i winload
path                    \WINDOWS\system32\winload.exe
```

## Windows System Initialization

#### 1. Loading Operating System Kernel

`bootmgfw.efi` reads a BCD (Boot Config Data) located in the EFI system partition.

Loads file `winload.efi`.

#### 2. Initializing the Kernel

Windows systems have the kernel named `Ntoskrnl.exe`.

- Loads Windows Registry
- Loads device drivers
- Starts system pagefile located at `C:\pagefile.sys`
- Loads `hal.dll`

Kernel then spawns `System`, which in turn spawns `smss.exe` and `csrss.exe`

## Starting Subsystem

`System` will always have PID of `4`.

`System` will spawn `smss.exe`

| ![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/006_windows_boot_process/pages/winboot1.png "Windows Boot Process") |
|:--:|

Session 0 is for security and high privilege processes such as services.

Session 1 is for user level processes.

```powershell
PS C:\Users\andy.dwyer> tasklist /fi "imagename eq csrss.exe"   

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
csrss.exe                      484 Services                   0      2,840 K
csrss.exe                      560                            1      2,496 K
csrss.exe                      376 Console                    3      2,336 K
csrss.exe                     7756                            4      7,980 K
```

## Relevance

- `System` has more permissions than the admin account.
- Represents the windows OS.
- Can be tricked into executing malicious commands via `services`.

## Windows Process Tree Basics

SYSTEM IDLE Process
- no visible parent
- should only ever be 1 of each
- in kernel mode ( created by NT OS Kernel )
- SYSTEM always has PID 4
- SYSTEM IDLE Process always has 1 threat per CPU

SMSS.EXE
- parent is SYSTEM (PID 4)
- should only ever be 1 running
- runs from \system32\smss.exe
- 1st user mode process started by Kernel
- launches WINLOGON.EXE, WININIT.EXE, and CSRSS.EXE , then SMSS.EXE exits

WINLOGON.EXE
- no parent (because SMSS.EXE launches it and then SMSS.EXE exits)
- runs as NT AUTHORITY\SYSTEM
- runs from \system32\winlogon.exe
- may spawn child processes (alternate login devices such as biometric readers)
- launches USERINIT.EXE which runs logon scripts, connects to network, starts EXPLORER.EXE

WININIT.EXE
- no parent (because SMSS.EXE launches it and then SMSS.EXE exits)
- runs as NT AUTHORITY\SYSTEM
- runs from system32\wininit.exe
- launches SERVICES.EXE, LSASS.EXE, and LSM.EXE
- creates %windir%\temp

CSRSS.EXE
- no parent (because SMSS.EXE launches it and then SMSS.EXE exits)
- runs as NT AUTHORITY\SYSTEM
- runs from system32\csrss.exe

USERINIT.EXE
- parent is WINLOGON.EXE
- Runs logon scripts, connects to network, starts EXPLORER.EXE, then exits

EXPLORER.EXE
- no parent (because USERINIT.EXE launches it and then USERINIT.EXE exits)
- runs from \windows\explorer.exe
- no TCP/IP network connections
- normally launches most user processes as children

SERVICES.EXE
- parent is WININIT.EXE
- runs as NT AUTHORITY\SYSTEM
- runs from \system32\services.exe
- normally multiple children processes as SVCHOST.EXE for each service

LSASS.EXE
- parent is WININIT.EXE
- always only 1 LSASS.EXE
- should NEVER spawn child processes
- runs as NT AUTHORITY\SYSTEM
- runs from \system32\lsass.exe

LSM.EXE
- parent is WININIT.EXE
- should NEVER spawn child processes
- runs as NT AUTHORITY\SYSTEM
- runs from \system32\lsm.exe

SVCHOST.EXE
- parent is SERVICES.EXE
- runs from \system32\svchost.exe
- runas as 1 of these accounts (NT AUTHORITY\SYSTEM, LOCAL SERVICE, or NETWORK SERVICE)
- command line always looks like "SVCHOST.EXE -k [name]"
