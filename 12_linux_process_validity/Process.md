# Linux Processes

# 1. (5)
Prompt:
```
What is the process ID (PID) of the SysV Init daemon?
```

Steps:
```bash
usacys@workstation02:~/Documents/CCTC/CCTC_Notes$ ps -elf | head
F S UID          PID    PPID  C PRI  NI ADDR SZ WCHAN  STIME TTY          TIME CMD
4 S root           1       0  0  80   0 - 42118 -      09:18 ?        00:00:01 /sbin/init splash
```

Answer:
```
1
```

# 2. (10)
Prompt:
```
How many child processes did SysV Init daemon spawn?
```

Steps:
```bash
bombadil@minas-tirith:~$ ps --ppid 1 -lf | wc -l
21
```

Answer:
```
21
```

# 3. (10)
Prompt:
```
Identify all of the arguments given to the ntpd daemon (service) using ps.

Format: List all options with parameters (include numbers).
```

Steps:
```bash
bombadil@minas-tirith:~$ ps -elf | grep ntpd
5 S ntp       1393     1  0  80   0 - 23949 -      Feb21 ?        00:01:05 /usr/sbin/ntpd -p /var/run
/ntpd.pid -g -u 105:109

bombadil@minas-tirith:~$ cat /proc/1393/cmdline | sed -e "s/\x00/ /g"; echo
/usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 105:109
```

Answer:
```
-p /var/run/ntpd.pid -g -u 105:109
```

# 4. (10)
Prompt:
```
What is the parent process to Bombadil’s Bash process?
```

Steps:
```bash
ps -elf
```

Answer:
```
sshd
```

# 5. (10)
Prompt:
```
Identify the file mapped to the fourth file descriptor (handle) of the cron process.

HINT: There might be multiple cron processes, but only one with the answer.

Flag format: /absolute/path
```

Steps:
```bash
bombadil@minas-tirith:~$ ps -elf | grep cron
1 S root      1356     1  0  80   0 -  5290 -      Feb21 ?        00:00:14 /usr/sbin/cron
0 S bombadil 28528 25998  0  80   0 -  3179 -      15:57 pts/0    00:00:00 grep cron     
bombadil@minas-tirith:~$ sudo ls -l /proc/1356/fd
total 0
lr-x------ 1 root root 64 Mar  7 15:22 0 -> /dev/null     
l-wx------ 1 root root 64 Mar  7 15:22 1 -> /dev/null     
l-wx------ 1 root root 64 Mar  7 15:22 2 -> /dev/null     
lrwx------ 1 root root 64 Mar  7 15:22 3 -> /run/crond.pid
```

Answer:
```
/run/crond.pid
```

# 6. (10)
Prompt:
```
Identify the permissions that cron has on the file identified in Processes 5.

HINT: Read the man page for lsof to understand permissions.

Flag format: If more than one, list the permissions comma separated, no spaces
```

Steps:
```bash
bombadil@minas-tirith:~$ ls -l /run/crond.pid
-rw-r--r-- 1 root root 5 Feb 21 21:03 /run/crond.pid
```

Answer:
```
read,write
```

# 7. (10)
Prompt:
```
Identify the names of the orphan processes on the SysV system.

NOTE: Remember, orphan processes spawn and die periodically. Try monitoring the processes list with top or htop to find them.

Flag format: in alphabetical order with all non-alphabetic characters removed: Name,Name,Name,Name

HINT: Only character names!
```

Steps:
```bash
29876 root       20   0  4028    72     0 S  0.0  0.0  0:00.00 Tolkien_____Main
29877 root       20   0  4028    72     0 S  0.0  0.0  0:00.00 Eowyn_______
29878 root       20   0  4028    72     0 S  0.0  0.0  0:00.00 Aragorn_____
29879 root       20   0  4028    72     0 S  0.0  0.0  0:00.00 BruceWayne__
```

Answer:
```
Aragorn,BruceWayne,Eowyn,Tolkien
```

# 8. (10)
Prompt:
```
Locate zombie processes on the SysV system.

Identify the zombie processes' parent process.

NOTE: Remember, zombie processes only live until the parent process kills and removes them from the system’s process table. Try monitoring the processes list with top or htop to find them.

Flag format: /absolute/path
```

Steps:
```bash
2509 root       20   0  4028   640   580 S  0.0  0.0  0:00.00 /bin/funk
2510 root       20   0     0     0     0 Z  0.0  0.0  0:00.00 ____Im___
2511 root       20   0     0     0     0 Z  0.0  0.0  0:00.00 ___Rick__
2512 root       20   0     0     0     0 Z  0.0  0.0  0:00.00 ___James_
```

Answer:
```
/bin/funk
```

# 9. (10)
Prompt:
```
Locate the strange open port on the SysV system.

Identify the command line executable and its arguments.

Flag format: /executable/path -arguments
```

Steps:
```bash
bombadil@minas-tirith:~$ sudo lsof -i -P -n
COMMAND   PID     USER   FD   TYPE   DEVICE SIZE/OFF NODE NAME
dhclient 1070     root    5u  IPv4    11277      0t0  UDP *:68
dhclient 1105     root    5u  IPv4    11338      0t0  UDP *:68
ntpd     1393      ntp   16u  IPv6    11793      0t0  UDP *:123
ntpd     1393      ntp   17u  IPv4    11798      0t0  UDP *:123
ntpd     1393      ntp   18u  IPv4    11803      0t0  UDP 127.0.0.1:123
ntpd     1393      ntp   19u  IPv4    11805      0t0  UDP 10.9.0.7:123
ntpd     1393      ntp   20u  IPv6    11807      0t0  UDP [::1]:123
ntpd     1393      ntp   24u  IPv6    11864      0t0  UDP [fe80::f816:3eff:fec2:930c]:123
sshd     1647     root    3u  IPv4    12401      0t0  TCP *:22 (LISTEN)
sshd     1647     root    4u  IPv6    12403      0t0  TCP *:22 (LISTEN)
netcat   1746     root    3u  IPv4    12257      0t0  TCP *:9999 (LISTEN)
sshd     1798     root    3u  IPv4 15813477      0t0  TCP 10.9.0.7:22->10.9.0.2:54649 (ESTABLISHED)  
sshd     1817 bombadil    3u  IPv4 15813477      0t0  TCP 10.9.0.7:22->10.9.0.2:54649 (ESTABLISHED)

bombadil@minas-tirith:~$ ps -elf
0 S root      1746     1  0  80   0 -  1575 -      Feb21 ?        00:00:00 /bin/netcat -lp 9999
```

Answer:
```
/bin/netcat -lp 9999
```
