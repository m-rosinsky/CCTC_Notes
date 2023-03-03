# Linux Boot Process

Start Key: ``

## The Linux Boot Proccess Overview

| ![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/007_linux_boot_process/pages/linboot1.png "Linux Boot Process") |
|:--:|

## BIOS and UEFI

UEFI benefits:
1. UEFI Firmware is loaded into flash memory or EEPROM.
2. UEFI offers SECURE BOOT mode which allows only verified drivers to load.
3. UEFI offers drive support of up to 9 zettabytes', while BIOS only works with 2 terabytes.
4. UEFI Boots much faster than BIOS systems, especially for Windows machines.

## 1st Stage Bootloaders

#### Master Boot Record (MBR)

Contains information on partitions locations on the hard drive.

Partitions contain the 2nd stage bootloader known as GRUB (Grand Unified Bootloader)

MBR is a boot sector.

The initial section of code that contains a bootloader called GRUB.

#### MBR Layout

First 512 bytes of hard drive contains MBR.

1. Bootstrap code.          (446 bytes)
2. Partition entries 1-4.   (16 bytes each)
3. Boot signature.          (2 bytes)

#### Locate the hard drive and partition table on Linux:

```bash
garviel@terra:~$ lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0      11:0    1   506K  0 rom
vda     252:0    0   128G  0 disk
├─vda1  252:1    0 127.9G  0 part /
├─vda14 252:14   0     4M  0 part
└─vda15 252:15   0   106M  0 part /boot/efi
```

```bash
root@terra:~$ sudo xxd -l 512 -g 1 /dev/vda
00000000: eb 63 90 00 00 00 00 00 00 00 00 00 00 00 00 00  .c..............
00000010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00000020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00000030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00000040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00000050: 00 00 00 00 00 00 00 00 00 00 00 80 00 08 00 00  ................
00000060: 00 00 00 00 ff fa 90 90 f6 c2 80 74 05 f6 c2 70  ...........t...p
00000070: 74 02 b2 80 ea 79 7c 00 00 31 c0 8e d8 8e d0 bc  t....y|..1......
00000080: 00 20 fb a0 64 7c 3c ff 74 02 88 c2 52 bb 17 04  . ..d|<.t...R...
00000090: f6 07 03 74 06 be 88 7d e8 17 01 be 05 7c b4 41  ...t...}.....|.A
000000a0: bb aa 55 cd 13 5a 52 72 3d 81 fb 55 aa 75 37 83  ..U..ZRr=..U.u7.
000000b0: e1 01 74 32 31 c0 89 44 04 40 88 44 ff 89 44 02  ..t21..D.@.D..D.
000000c0: c7 04 10 00 66 8b 1e 5c 7c 66 89 5c 08 66 8b 1e  ....f..\|f.\.f..
000000d0: 60 7c 66 89 5c 0c c7 44 06 00 70 b4 42 cd 13 72  .|f.\..D..p.B..r
000000e0: 05 bb 00 70 eb 76 b4 08 cd 13 73 0d 5a 84 d2 0f  ...p.v....s.Z...
000000f0: 83 d0 00 be 93 7d e9 82 00 66 0f b6 c6 88 64 ff  .....}...f....d.
00000100: 40 66 89 44 04 0f b6 d1 c1 e2 02 88 e8 88 f4 40  @f.D...........@
00000110: 89 44 08 0f b6 c2 c0 e8 02 66 89 04 66 a1 60 7c  .D.......f..f..|
00000120: 66 09 c0 75 4e 66 a1 5c 7c 66 31 d2 66 f7 34 88  f..uNf.\|f1.f.4.
00000130: d1 31 d2 66 f7 74 04 3b 44 08 7d 37 fe c1 88 c5  .1.f.t.;D.}7....
00000140: 30 c0 c1 e8 02 08 c1 88 d0 5a 88 c6 bb 00 70 8e  0........Z....p.
00000150: c3 31 db b8 01 02 cd 13 72 1e 8c c3 60 1e b9 00  .1......r.......
00000160: 01 8e db 31 f6 bf 00 80 8e c6 fc f3 a5 1f 61 ff  ...1..........a.
00000170: 26 5a 7c be 8e 7d eb 03 be 9d 7d e8 34 00 be a2  &Z|..}....}.4...
00000180: 7d e8 2e 00 cd 18 eb fe 47 52 55 42 20 00 47 65  }.......GRUB .Ge
00000190: 6f 6d 00 48 61 72 64 20 44 69 73 6b 00 52 65 61  om.Hard Disk.Rea
000001a0: 64 00 20 45 72 72 6f 72 0d 0a 00 bb 01 00 b4 0e  d. Error........
000001b0: cd 10 ac 3c 00 75 f4 c3 00 00 00 00 00 00 00 00  ...<.u..........
000001c0: 02 00 ee ff ff ff 01 00 00 00 ff ff ff 0f 00 00  ................
000001d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
000001e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
000001f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa  ..............U.
```

#### GUID Partition Tables (GPT)

GPT has a few advantages over MBR:
1. GPT Only works with UEFI Firmware
2. GPT has many boot sectors stored around the disk as redundancy so an issue in one will not deadline the entire machine
3. GPT supports 128(and more depending on Operating System) separate physical partitions, while MBR supports only 4
4. GPT Supports partitions up to 9 zettabytes. Which is ridiculous.

## 2nd Stage Bootloader (GRUB)

GRUB stage 2 is inside the selected active paritition mounted in `/boot` or
a completely separate partition.

#### On BIOS using MBR

1. `boot.img` located in the first 440 bytes of the MBR
2. `core.img` located in the MBR between bootstrap and first partition
3. `/boot/grub/i386-pc/normal.mod` loads GRUB menu
4. `/boot/grub/grub.cfg` displays list of kernels to load

#### On UEFI using GPT

1. `grubx64.efi` located in EFI partition or `/boot`
2. `/boot/grub/x64_64-efi/normal.mod`
3. `boot/grub/grub.cfg`

#### Looking at GRUB config to find Kernel

```
student@linux-opstation-kspt:/$ cat /boot/grub/grub.cfg
_truncated_
set linux_gfx_mode=auto
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-LABEL=cloudimg-rootfs' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  6c0fba3b-b236-4b3a-b999-db7359c5d220
        else
          search --no-floppy --fs-uuid --set=root 6c0fba3b-b236-4b3a-b999-db7359c5d220
        fi
        linux   /boot/vmlinuz-4.15.0-76-generic root=LABEL=cloudimg-rootfs ro  console=tty1 console=ttyS0
        initrd  /boot/initrd.img-4.15.0-76-generic
_truncated_
```

## Linux Kernel

Monolithic Kernel

System calls all functionality to the user.

`ltrace` will show library calls from the C++ shared object library.

## Init

Once the kernel is loaded, it is hard coded to execute `/sbin/init`.

#### SysV

Legacy system init method.

Uses `/etc/init` program, then reads `/etc/inittab` to create processes in groups.

Groups are called _RUN LEVELS_.

Run levels are defined in `/etc/rc.d/rc*.d`

#### Run Levels

Run levels in SysV are a series of programs that start or kill background processes
at specific run levels.

```
root@terra:~# ls -l /etc/rc3.d
total 0
lrwxrwxrwx 1 root root 29 Feb 28  2022 K01apache-htcacheclean -> ../init.d/apache-htcacheclean
lrwxrwxrwx 1 root root 15 Mar  4  2020 S01acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root 17 Feb 28  2022 S01apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root 16 Mar  4  2020 S01apport -> ../init.d/apport
lrwxrwxrwx 1 root root 13 Mar  4  2020 S01atd -> ../init.d/atd
lrwxrwxrwx 1 root root 24 Feb 28  2022 S01binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root 26 Mar  4  2020 S01console-setup.sh -> ../init.d/console-setup.sh      
lrwxrwxrwx 1 root root 14 Mar  4  2020 S01cron -> ../init.d/cron
lrwxrwxrwx 1 root root 14 Mar  4  2020 S01dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root 21 Mar  4  2020 S01grub-common -> ../init.d/grub-common
lrwxrwxrwx 1 root root 20 Mar  4  2020 S01irqbalance -> ../init.d/irqbalance
lrwxrwxrwx 1 root root 22 Mar  4  2020 S01lvm2-lvmetad -> ../init.d/lvm2-lvmetad
lrwxrwxrwx 1 root root 23 Mar  4  2020 S01lvm2-lvmpolld -> ../init.d/lvm2-lvmpolld
lrwxrwxrwx 1 root root 15 Mar  4  2020 S01lxcfs -> ../init.d/lxcfs
lrwxrwxrwx 1 root root 13 Mar  4  2020 S01lxd -> ../init.d/lxd
lrwxrwxrwx 1 root root 15 Mar  4  2020 S01mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 23 Mar  4  2020 S01open-vm-tools -> ../init.d/open-vm-tools
lrwxrwxrwx 1 root root 18 Mar  4  2020 S01plymouth -> ../init.d/plymouth
lrwxrwxrwx 1 root root 15 Mar  4  2020 S01rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root 17 Mar  4  2020 S01rsyslog -> ../init.d/rsyslog
lrwxrwxrwx 1 root root 13 Mar  4  2020 S01ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root 29 Mar  4  2020 S01unattended-upgrades -> ../init.d/unattended-upgrades
lrwxrwxrwx 1 root root 15 Mar  4  2020 S01uuidd -> ../init.d/uuidd
```

This system is Systemd
```
root@terra:~# ps --no-headers -o comm 1
systemd
```
