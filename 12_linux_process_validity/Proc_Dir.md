# Linux Process Proc Dir

# 1. (10)
Prompt:
```
Examine the process list to find the ssh process. Then, identify the symbolic link to the absolute path for its executable in the /proc directory.

The flag is the absolute path to the symbolic link, and the file it is linked to.

Flag format: /absolute/path,/absolute/path
```

Steps:
```
ps -elf | grep ssh

sudo ls -lrt /proc/1647
lrwxrwxrwx 1 root root 0 Mar  7 15:22 exe -> /usr/sbin/sshd
```

Answer:
```
/proc/1647/exe,/usr/sbin/sshd
```

# 2. (10)
Prompt:
```
Identify the file that contains udp connection information. Identify the process using port 123.

For the flag, enter:

    Process name
    File descriptor number for the udp socket
    Its permissions as shown in lsof

Flag format: name,#,permission
```

Steps:
```
bombadil@minas-tirith:~$ sudo lsof -i -P -n
COMMAND   PID     USER   FD   TYPE   DEVICE SIZE/OFF NODE NAME
ntpd     1393      ntp   16u  IPv6    11793      0t0  UDP *:123

bombadil@minas-tirith:~$ ps -elf | grep 1393
5 S ntp       1393     1  0  80   0 - 23949 -      Feb21 ?        00:01:06 /usr/sbin/ntpd -p /var/run
/ntpd.pid -g -u 105:109
```

Answer:
```
ntp,19,u
```

# 3. (15)
Prompt:
```
Identify one of the human-readable file handles by the other program that creates a zombie process.

NOTE: Remember, zombie processes only live until the parent process kills them. Try monitoring the processes list with top or htop to find them.

The flag is the text from one of the files it reads.
```

Steps:
```
1745 root       20   0  4028   828   760 S  0.0  0.0  0:02.43 /sauron
1746 root       20   0  6300  1660  1552 S  0.0  0.1  0:00.00 /bin/netcat -lp 9999

7603 root       20   0  4028   644   584 S  0.0  0.0  0:00.00 /usr/local/bin/thenine
7604 root       20   0  4160    68     0 S  0.0  0.0  0:00.00 ________Nazgul________
7605 root       20   0     0     0     0 Z  0.0  0.0  0:00.00 thenine

bombadil@minas-tirith:/proc$ strings /usr/local/bin/thenine
//opt//mysoul

cat /opt/mysoul

```

Answer:
```
ntp,19,u
```
