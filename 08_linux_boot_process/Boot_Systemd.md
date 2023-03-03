# Linux Boot Systemd

# 1. (10)
Prompt:
```
Identify the file symbolically-linked to init on the SystemD init machine.

Flag format: /absolute/path

Reminder: Use your Terra machine for these SystemD challenges!
```

Steps:
```bash
garviel@terra:~$ file /sbin/init
/sbin/init: symbolic link to /lib/systemd/systemd
```

Answer:
```
/lib/systemd/systemd
```

# 2. (10)
Prompt:
```
What is the default target on the SystemD machine and where is it actually located?

Flag format: name.target,/absolute/path

NOTE: Use the SystemD Machine for this question.
```

Steps:
```bash
garviel@terra:~$ ls -lisa /lib/systemd/system/default.target
16777 0 lrwxrwxrwx 1 root root 16 Sep  6 03:18 /lib/systemd/system/default.target -> graphical.target

garviel@terra:~$ find / -name "graphical.target" 2>/dev/null
/lib/systemd/system/graphical.target
```

Answer:
```
graphical.target,/lib/systemd/system/graphical.target
```

# 3. (10)
Prompt:
```
What unit does the graphical.target want to start, based solely on its configuration file?

HINT: Targets deal with which init system? Which machine should you be looking for this flag, on?

NOTE: Use the SystemD Machine for this question.
```

Steps:
```bash
garviel@terra:~$ cat /lib/systemd/system/graphical.target
#  SPDX-License-Identifier: LGPL-2.1+
#
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.

[Unit]
Description=Graphical Interface
Documentation=man:systemd.special(7)
Requires=multi-user.target
Wants=display-manager.service
Conflicts=rescue.service rescue.target
After=multi-user.target rescue.service rescue.target display-manager.service
AllowIsolate=yes
```

Answer:
```
display-manager.service
```

# 4. (10)
Prompt:
```
What dependency to graphical.target will stop it from executing if it fails to start, based solely on its static configuration file?

NOTE: Use the SystemD Machine for this question.
```

Steps:
```bash
garviel@terra:~$ cat /lib/systemd/system/graphical.target
#  SPDX-License-Identifier: LGPL-2.1+
#
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.

[Unit]
Description=Graphical Interface
Documentation=man:systemd.special(7)
Requires=multi-user.target
Wants=display-manager.service
Conflicts=rescue.service rescue.target
After=multi-user.target rescue.service rescue.target display-manager.service
AllowIsolate=yes
```

Answer:
```
multi-user.target
```

# 5. (10)
Prompt:
```
How many wants dependencies does SystemD actually recognize for the default.target

HINT: Use the systemctl command with some arguments to make life easier.

Flag format: #

NOTE: Use the SystemD Machine for this question.
```

Steps:
```bash
garviel@terra:~$ systemctl show -p Wants graphical.target | tr " " "\n"
Wants=grub-common.service
systemd-update-utmp-runlevel.service
apport.service
accounts-daemon.service
display-manager.service
vestrisecreta.service
ureadahead.service
garviel@terra:~$ systemctl show -p Wants graphical.target | tr " " "\n" | wc -l
7
```

Answer:
```
7
```

# 6. (10)
Prompt:
```
What is the full path to the binary used for standard message logging?

HINT: Standard message logging is standardized across UNIX systems.

NOTE: As the challenge name suggests, use the SystemD machine for this question.

Flag format: /absolute/path
```

Steps:
```bash
garviel@terra:~$ find / -name "*syslogd*" 2>/dev/null
/etc/apparmor.d/usr.sbin.rsyslogd
/etc/apparmor.d/disable/usr.sbin.rsyslogd
/etc/apparmor.d/local/usr.sbin.rsyslogd
/run/rsyslogd.pid
/usr/share/man/man8/rsyslogd.8.gz
/usr/sbin/rsyslogd
```

Answer:
```
/usr/sbin/rsyslogd
```

# Grub. (10)
Prompt:
```
What is the full path to the binary used for standard message logging?

HINT: Standard message logging is standardized across UNIX systems.

NOTE: As the challenge name suggests, use the SystemD machine for this question.

Flag format: /absolute/path
```

Steps:
```bash
garviel@terra:~$ cat /boot/grub/grub.cfg
menuentry 'Debian GNU/Linux, with Linux 4.9.0-12-amd64 (recovery mode)' --class debian --class gn
u-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.9.0-12-amd64-recovery-cdd695b0-e558-4915-
ba1d-38c769fee1b1' {
         load_video
         insmod gzio
         if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
         insmod part_msdos
         insmod ext2
         if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root  cdd695b0-e558-4915-ba1d-38c769fee1b1
         else
           search --no-floppy --fs-uuid --set=root cdd695b0-e558-4915-ba1d-38c769fee1b1
         fi
         echo    'Loading Linux 4.9.0-12-amd64 ...'
         linux /boot/vmlinuz-4.9.0-12-amd64 root=UUID=cdd695b0-e558-4915-ba1d-38c769fee1b1 ro single
         echo    'Loading initial ramdisk ...'
         initrd  /boot/initrd.img-4.9.0-12-amd64
 }
}


# /boot/vmlinuz-4.9.0-12-amd64
```

Answer:
```
linux,/boot/vmlinuz-4.9.0-12-amd64
```
