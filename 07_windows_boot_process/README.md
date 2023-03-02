# Windows Boot Process

Start Key: ``

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
