# Windows Boot Process

Start Key: ``

## BIOS and UEFI

Windows Boot Process
| ![alt text](http://1.bp.blogspot.com/-MaRtDTHH1Vo/UysJF8KXNbI/AAAAAAAAALo/D6Kt2f8Gpmo/s1600/Walkthrough_Diagram.jpg "Windows Boot Process") |
|:--:|

1. Hardware Init.
2. Load boot sector or boot manager.
3. Loading the OS from the boot sector.

#### Security in Boot

- Rootkits can hide themselves in the boot process.
- Bootkits replace the OS bootloader to load the bootkit before the OS.
