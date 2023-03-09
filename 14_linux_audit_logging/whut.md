# Linux Auditing and Logging Whut

# 1. (10)
Prompt:
```
How many unique users logged into this machine?
```

Steps:
```
garviel@terra:~$ cat log.txt | grep login
Apr 6 00:00:03 linux-opstation-7qhp systemd-logind[993]: New session 189 of user Frodo.
Apr 6 09:35:52 linux-opstation-7qhp systemd-logind[993]: New session 190 of user Balrog.
Apr 6 13:34:19 linux-opstation-7qhp systemd-logind[993]: New session 200 of user Saruman.
Apr 6 13:58:22 linux-opstation-7qhp systemd-logind[993]: New session 201 of user Saruman.
```

Answer:
```
3
```

# 2. (10)
Prompt:
```
What is the total amount of time users were logged into the machine?

Flag format: #h,#m (Replace the # with a number)
```

Steps:
```
garviel@terra:~$ cat log.txt | grep Disconnected
Apr 6 01:15:02 linux-opstation-7qhp[3915]: Disconnected from user Frodo 192.168.242.166 port 48558   
Apr 6 10:26:41 linux-opstation-7qhp[3915]: Disconnected from user Balrog 192.16.6.6 port 48557       
Apr 6 13:53:21 linux-opstation-7qhp[3915]: Disconnected from user Saruman 192.17.7.7 port 48559      
Apr 6 13:53:29 linux-opstation-7qhp[3915]: Disconnected from user Saruman 192.17.7.7 port 48559      
Apr 6 16:43:21 linux-opstation-7qhp[3915]: Disconnected from user Saruman 12.100.80.12 port 9875

1 15
0 51
0 19
2 45

5 10
```

Answer:
```
5h,10m
```

# 3. (10)
Prompt:
```
Identify the Cyber Attack Technique that Balrog is trying on the machine.

HINT: https://attack.mitre.org/
```

Steps:
```
Apr 6 10:05:02 linux-opstation-7qhp sudo: Balrog : command not allowed ; TTY=pts/0 ; PWD=/home/Balro
 ; USER=root ; COMMAND=cat /etc/shadow > shadowed
Apr 6 10:11:40 linux-opstation-7qhp sudo: pam_unix(sudo:auth): auth could not identify password for  
Balrog]
Apr 6 10:11:41 linux-opstation-7qhp sudo: Balrog : command not allowed ; TTY=pts/0 ; PWD=/home/Balro
 ; USER=root ; COMMAND=apt install john -y
```

Answer:
```
Credential access
```

# 4. (15)
Prompt:
```
What user successfully executed commands?
```

Answer:
```
Saruman
```

# 5. (15)
Prompt:
```
Analyze the file to determine when a shell was spawned as a different user and how long it was maintained for.

    Provide the :
        duration the shell was maintained
        the command used to create it
        number of times they [successfully] escalated

Flag Format: #h,#m,command,number of times

    Round minutes up to the closest number divisible by 10.
```

Steps:
```
Apr 6 13:35:51 linux-opstation-7qhp sudo: Saruman : TTY=pts/0 ; PWD=/home/Saruman ; USER=root ; COMMA
ND=find /etc/passwd -exec /bin/sh {} ;\

Apr 6 13:37:31 linux-opstation-7qhp sudo: Saruman : TTY=pts/0 ; PWD=/home/Saruman ; USER=root ; COMMA
ND=find /etc/passwd -exec /bin/sh {} ;\

Apr 6 14:13:21 linux-opstation-7qhp sudo: Saruman : TTY=pts/0 ; PWD=/home/Saruman ; USER=root ; COMMA
ND=find /etc/passwd -exec /bin/sh ;\
Apr 6 14:13:22 linux-opstation-7qhp sudo: pam_unix(sudo:session): session opened for user root by Sar
uman(uid=0)
Apr 6 14:13:37 linux-opstation-7qhp systemd: pam_unix(systemd-user:session): session opened for user
Saruman by (uid=0)
Apr 6 14:13:38 linux-opstation-7qhp sudo: Saruman : TTY=pts/0 ; PWD=/home/Saruman ; USER=root ; COMMA
ND=find /etc/passwd -exec /bin/sh ;\
Apr 6 14:13:39 linux-opstation-7qhp sudo: pam_unix(sudo:session): session opened for user root by Sar
uman(uid=0)
Apr 6 14:15:00 linux-opstation-7qhp systemd: pam_unix(systemd-user:session): session opened for user
Saruman by (uid=0)
Apr 6 14:15:01 linux-opstation-7qhp sudo: Saruman : TTY=pts/0 ; PWD=/home/Saruman ; USER=root ; COMMA
ND=find /etc/passwd -exec /bin/sh \;
Apr 6 14:15:02 linux-opstation-7qhp sudo: pam_unix(sudo:session): session opened for user root by Sar
uman(uid=0)
Apr 6 14:15:20 linux-opstation-7qhp systemd: pam_unix(systemd-user:session): session opened for user
Saruman by (uid=0)
Apr 6 14:15:21 linux-opstation-7qhp sudo: Saruman : TTY=pts/0 ; PWD=/home/Saruman ; USER=root ; COMMA
ND=find /etc/passwd -exec /bin/sh \;
Apr 6 14:15:22 linux-opstation-7qhp sudo: pam_unix(sudo:session): session opened for user root by Sar
uman(uid=0)
Apr 6 16:43:21 linux-opstation-7qhp[3915]: Disconnected from user Saruman 12.100.80.12 port 9875

Command: find /etc/passwd -exec /bin/sh ;\

Opened: 13:35:21
Closed: 16:43:21

Duration: 3h,08m

Times: 2
```

Answer:
```
2h,30m,find /etc/passwd -exec /bin/sh \;,2
```
