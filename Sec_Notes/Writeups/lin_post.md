# Linux Post Exploitation

Scheme:
```
> jump
-> Pivot: 192.168.28.105
--> T1: 192.168.28.27
--> T2: 192.168.28.12
```

Pivot:
```
Hostname: Donovian-Terminal
IP: 192.168.28.105
OS: Ubuntu 18.04
Creds: comrade :: StudentReconPassword
Last Known SSH Port: 2222
PSP: rkhunter
```

T1:
```
IP: 192.168.28.27
Creds: comrade :: StudentPrivPassword
```

T2:
```
IP: 192.168.28.12
Creds: comrade :: StudentPrivPassword
```

## Enumerate

Nmap:
```
Nmap scan report for 192.168.28.27
Host is up (0.0020s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for 192.168.28.12
Host is up (0.0021s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
```

## Escalate

shadow:
```
root:$6$/3RL8PUH$VdeUuKr75jSALs9jmLTGKMzxkZvhsRzmPsiCYM9cg.AODP1YgA.JWajSkknNxI0ptS/pK8PIOXMaXcvd3IgRT.:18934:0:99999:7:::
zeus:$6$V34Nv7Ib$.PZChAQgzH9FMTfoUN0X3Y2mUIT3/rXju7cmXa2mAVTAZscB48slP8A333kYxrtlPzMLN9yEd5wZnQJe4Wzbz/:18934:0:99999:7:::
daemon:*:18325:0:99999:7:::
bin:*:18325:0:99999:7:::
sys:*:18325:0:99999:7:::
sync:*:18325:0:99999:7:::
games:*:18325:0:99999:7:::
man:*:18325:0:99999:7:::
lp:*:18325:0:99999:7:::
mail:*:18325:0:99999:7:::
news:*:18325:0:99999:7:::
uucp:*:18325:0:99999:7:::
proxy:*:18325:0:99999:7:::
www-data:*:18325:0:99999:7:::
backup:*:18325:0:99999:7:::
list:*:18325:0:99999:7:::
irc:*:18325:0:99999:7:::
gnats:*:18325:0:99999:7:::
nobody:*:18325:0:99999:7:::
systemd-network:*:18325:0:99999:7:::
systemd-resolve:*:18325:0:99999:7:::
syslog:*:18325:0:99999:7:::
messagebus:*:18325:0:99999:7:::
_apt:*:18325:0:99999:7:::
lxd:*:18325:0:99999:7:::
uuidd:*:18325:0:99999:7:::
dnsmasq:*:18325:0:99999:7:::
landscape:*:18325:0:99999:7:::
sshd:*:18325:0:99999:7:::
pollinate:*:18325:0:99999:7:::
ubuntu:!:18934:0:99999:7:::
comrade:$6$EabwO.sc$zT1xo.vDKK209IDOiZjDIXoc8YGU2ljT/LEE8i.pG0bO1xvHMTsZQKGkBAuDqZ4r7Xk4dNJzIVFe6VdzLt8PT0:18934:0:99999:7:::
billybob:$6$je9YkJOP$Jdu6dFuwkqS3Qg5xT.2dq9elEU9b0.ybTaXwIYFnqn9g/k0h.n1PtUOROf28gVVxNzYJ4z8.uw7ve9BTD7t611:18934:0:99999:7:::
bobby:$6$ryRQEt/S$lTxP9YSMV4NllvVwpHyw4I.sgl7a4htNeKgzHeGNyhXKLtLgTBF2rYd9y.fcO3cgA2cBL8RrwRIL1yrwSPbM7.:18934:0:99999:7:::
jerry:$6$YMWB7T6W$7f2Nx71Tt4eNDBuBeo6H.kjs93nIRD1j924GWZ.s/Xp5FNgo3JzJowgOhQ.8LkHcYFNuY1l4m3EJ5Br0FQMiU0:18934:0:99999:7:::
jimmy:$6$h5lL6ckI$cL.Oei4ZvvG2iyiaD2HK09MVFpa0NGUZkVF5FSewC42NlNt2//I/FrzA0o3LXGZRlGck004K1i08CWpnkLj2l1:18934:0:99999:7:::
sarah:$6$CBpHvShR$1CIKzlI9glGDyBDzoisnOBBvWBYAjlmGeqOPLrncAxFh6Ylvda3o31amBxtiU/L3XgjoZVCFjhW1.cv40MHwm/:18934:0:99999:7:::
wendy:$6$p596ZHHF$Tse1FrfiLQQaAxxqlZpbYe9c3n6qZbzQmiGcuCFv8IwcvqC0v8422.mw4mR.dBKMQTNbq5/sj/c9VIV3JncNB0:18934:0:99999:7:::
```

```
zeus:ghjcnbnenrf:0:0:zeus:/root:/bin/bash
```
