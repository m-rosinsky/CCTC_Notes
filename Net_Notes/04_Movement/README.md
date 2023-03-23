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
