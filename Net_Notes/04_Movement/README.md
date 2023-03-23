# Movement

ssh net2_student12@10.50.30.212 -p 25
password: password12

FTP -> 10.0.0.104
username: anonymous
password:

## Dynamic Tunneling

From Internet Host:
```
ssh net2_student12@10.50.30.212 -p 25 -D 9050 -NT
```

This sets up a pivot on the intermediate machine.

```bash
# Potentially add -p
proxychains ftp 10.0.0.104
```

Restart SSH on diff port.
```
sudo vi /etc/ssh/sshd_config

sudo systemctl restart ssh
```

From Intermediate:
```
scp -3 student@10.10.0.40:flag.png student@192.168.1.10:
```

## Tunnel
Local Port Forward:
```
# TO PRIV HOST
IH$ ssh student@172.16.82.106 -p 2222 -L 1024:192.168.1.10:22

# TO BLUE HOST
IH$ ssh student@172.16.82.106 -p 2222 -L 1025:localhost:2222
```

```
IH$ scp -P 1024 flag.png student@localhost:
IH$ scp -P 1024 student@localhost:flag.png .
```

Dynamic:
```
IH$ ssh student@172.16.82.106 -p 2222 -D 9050 -NT
```

FIFO:
```
student@blue-host-1-student-12:~$ mkfifo pipe
student@blue-host-1-student-12:~$ nc -lvp 1111 < pipe | nc -lvp 4444 > pipe
```
