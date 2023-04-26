# Linux Post Exploitation Notes

## Commands

Date and Time:
```bash
$ date & time
```

w:
```
student@lin-ops:~$ w
 12:56:47 up 35 days, 23:31,  1 user,  load average: 0.00, 0.04, 0.01
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
student  pts/0    192.168.243.218  12:43   13:18   2.82s  0.00s dbus-launch --autolaunch=0bfd01fafb31495
```

last:
```
student@lin-ops:~$ last
student  pts/0        192.168.243.218  Wed Apr 19 12:43   still logged in
student  pts/0        192.168.243.218  Tue Apr 18 12:53 - 15:12  (02:19)
student  pts/0        192.168.243.218  Tue Apr 18 12:18 - 12:47  (00:28)
student  pts/0        192.168.243.218  Mon Apr 17 12:25 - 17:49  (05:24)
student  pts/0        192.168.243.218  Thu Apr 13 13:53 - 12:16  (22:23)
student  pts/0        192.168.243.218  Thu Apr 13 12:28 - 12:40  (00:12)
student  pts/0        192.168.243.218  Wed Apr 12 12:31 - 16:58  (04:26)
student  pts/0        192.168.243.218  Tue Apr 11 12:45 - 12:12  (23:27)
student  pts/0        192.168.243.218  Fri Apr  7 12:15 - 17:31  (05:15)
student  pts/0        192.168.243.218  Thu Apr  6 17:08 - 18:27  (01:18)
student  pts/0        192.168.243.218  Thu Apr  6 12:31 - 15:18  (02:46)
```

uptime:
```
student@lin-ops:~$ uptime
 12:59:35 up 35 days, 23:33,  1 user,  load average: 0.00, 0.02, 0.00
```

uname -a
```
student@lin-ops:~$ uname -a
Linux lin-ops 4.15.0-200-generic #211-Ubuntu SMP Thu Nov 24 18:16:04 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

lsof (look at files associated with processes)
