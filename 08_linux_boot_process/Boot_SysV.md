# Linux Boot SysV

# 1. (5)
Prompt:
```
Identify which of your Linux machines is using SysV Initialization.
```

Answer:
```
minas-tirith
```

# 2. (5)
Prompt:
```
Identity the default run level on the SysV Init Linux machine.

Flag format: #
```

Steps:
```bash
bombadil@minas-tirith:~$ cat /etc/inittab
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $        

# The default runlevel.
id:2:initdefault:
```

Answer:
```
2
```

# 3. (5)
Prompt:
```
What is the last script to run when the command init 6 is executed?

Flag format: /absolute/path

NOTE: Use the machine identified in SysV 1 for this question.
```

Steps:
```bash
bombadil@minas-tirith:~$ ls -l /etc/rc6.d
total 4
lrwxrwxrwx 1 root root  19 Oct 13  2021 K01cgmanager -> ../init.d/cgmanager
lrwxrwxrwx 1 root root  17 Oct 13  2021 K01cgproxy -> ../init.d/cgproxy
lrwxrwxrwx 1 root root  22 Feb  9  2020 K01cloud-config -> ../init.d/cloud-config
lrwxrwxrwx 1 root root  21 Feb  9  2020 K01cloud-final -> ../init.d/cloud-final
lrwxrwxrwx 1 root root  20 Feb  9  2020 K01cloud-init -> ../init.d/cloud-init
lrwxrwxrwx 1 root root  26 Feb  9  2020 K01cloud-init-local -> ../init.d/cloud-init-local
lrwxrwxrwx 1 root root  20 Feb  9  2020 K01irqbalance -> ../init.d/irqbalance
lrwxrwxrwx 1 root root  15 Feb  9  2020 K01unscd -> ../init.d/unscd
lrwxrwxrwx 1 root root  17 Oct 13  2021 K01urandom -> ../init.d/urandom
lrwxrwxrwx 1 root root  18 Oct 13  2021 K02sendsigs -> ../init.d/sendsigs
lrwxrwxrwx 1 root root  17 Oct 13  2021 K03rsyslog -> ../init.d/rsyslog
lrwxrwxrwx 1 root root  20 Oct 13  2021 K04hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx 1 root root  22 Oct 13  2021 K04umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx 1 root root  20 Oct 13  2021 K05networking -> ../init.d/networking
lrwxrwxrwx 1 root root  18 Oct 13  2021 K06umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root  20 Oct 13  2021 K07umountroot -> ../init.d/umountroot
lrwxrwxrwx 1 root root  16 Oct 13  2021 K08reboot -> ../init.d/reboot
-rw-r--r-- 1 root root 351 Feb 12  2017 README
```

Answer:
```
/etc/init.d/reboot
```

# 4. (5)
Prompt:
```
What run levels start the daemon that allows remote connections over port 22?

Flag format: #,#,#,#

NOTE: Use the machine identified in SysV 1 for this question.
```

Steps:
```bash
bombadil@minas-tirith:~$ ls -l /etc/rc1.d | grep ssh
bombadil@minas-tirith:~$ ls -l /etc/rc2.d | grep ssh
lrwxrwxrwx 1 root root  13 Oct 13  2021 S03ssh -> ../init.d/ssh
bombadil@minas-tirith:~$ ls -l /etc/rc3.d | grep ssh
lrwxrwxrwx 1 root root  13 Oct 13  2021 S03ssh -> ../init.d/ssh
bombadil@minas-tirith:~$ ls -l /etc/rc4.d | grep ssh
lrwxrwxrwx 1 root root  13 Oct 13  2021 S03ssh -> ../init.d/ssh
bombadil@minas-tirith:~$ ls -l /etc/rc5.d | grep ssh
lrwxrwxrwx 1 root root  13 Oct 13  2021 S03ssh -> ../init.d/ssh
bombadil@minas-tirith:~$ ls -l /etc/rc6.d | grep ssh
```

Answer:
```
2,3,4,5
```
