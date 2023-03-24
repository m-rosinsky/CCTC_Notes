# Tunnel Demo

IP: `10.50.31.162`

SSH Credentials:
```
net2_student12
student12
```

## NMAP SCAN:
```
nmap -sC -sV 10.50.31.162

Starting Nmap 7.70 ( https://nmap.org ) at 2023-03-24 12:52 UTC
Nmap scan report for 10.50.31.162
Host is up (0.00060s latency).
Not shown: 997 closed ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp
| fingerprint-strings:
|   GenericLines:
|     220 ProFTPD Server (Debian) [::ffff:104.16.181.1]
|     Invalid command: try being more creative
|     Invalid command: try being more creative
|   RTSPRequest, SMBProgNeg:
|_    220 ProFTPD Server (Debian) [::ffff:104.16.181.1]
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: PASV IP 104.16.181.1 is not the same as 10.50.31.162
22/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey:
|   2048 e3:f5:3e:75:3a:8a:30:67:ab:ec:e9:a5:7a:b9:22:ab (RSA)
|   256 7c:30:ff:62:9f:47:c1:4f:32:48:bf:54:55:9a:d7:a4 (ECDSA)
|_  256 ba:06:57:6a:6c:10:f4:16:a8:34:71:85:08:82:ea:86 (ED25519)
80/tcp open  http    nginx 1.14.2
|_http-server-header: nginx/1.14.2
|_http-title: Site doesn't have a title (text/html).
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

## SSH RECON:
```
ip addr: 104.16.181.1/27
```

```
ss -anltp
State        Recv-Q       Send-Q             Local Address:Port              Peer Address:Port       
LISTEN       0            128                      0.0.0.0:80             0.0.0.0:*          
LISTEN       0            128                      0.0.0.0:22             0.0.0.0:*          
LISTEN       0            1                   104.16.181.1:39591          0.0.0.0:*          
LISTEN       0            128                         [::]:80                [::]:*          
LISTEN       0            128                            *:21                   *:*          
LISTEN       0            128                         [::]:22                [::]:*

ss -antp (SEE ESTABLISHED CONNECTIONS)
```

```
ip nei | grep -v "FAILED"
104.16.181.30 dev eth0 lladdr fa:16:3e:9f:c5:13 REACHABLE
104.16.181.15 dev eth0 lladdr fa:16:3e:20:06:25 STALE
```

## SHARED FOLDER

```
net2_student12@john:~$ cd /usr/share/cctc
net2_student12@john:/usr/share/cctc$ ls
```

## TUNNELS
```
IH$ ssh net2_student12@10.50.31.162 -D 9050 -NT
```

NMAP:
```
IH$ proxychains nmap 104.16.181.15 -oN 10.15.181.15_nmap
# Nmap 7.70 scan initiated Fri Mar 24 13:16:29 2023 as: nmap -oN 104.16.181.15_nmap 104.16.181.15
Nmap scan report for 104.16.181.15
Host is up (0.0010s latency).
Not shown: 997 closed ports
PORT   STATE SERVICE
21/tcp open  ftp
22/tcp open  ssh
80/tcp open  http

# Nmap done at Fri Mar 24 13:16:30 2023 -- 1 IP address (1 host up) scanned in 1.23 seconds
```

WGET:
```
proxychains wget -r http://104.16.181.15
```

SSH:
```
jack$ ip addr
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc pfifo_fast state UP group default qlen 1000
    link/ether fa:16:3e:20:06:25 brd ff:ff:ff:ff:ff:ff
    inet 104.16.181.15/27 brd 104.16.181.31 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::f816:3eff:fe20:625/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc pfifo_fast state UP group default qlen 1000
    link/ether fa:16:3e:fc:ba:0e brd ff:ff:ff:ff:ff:ff
    inet 142.16.8.55/27 brd 142.16.8.63 scope global eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::f816:3eff:fefc:ba0e/64 scope link
       valid_lft forever preferred_lft forever
```

## JACK TUNNEL:
```
IH$ ssh net2_student12@10.50.31.162 -L 21201:104.16.181.15:22 -NT
```

## SCAN:
```
IH$ proxychains nmap 142.16.8.32/27 -p21-23,80 -Pn -oN jack_int_nmap

Nmap scan report for 142.16.8.41
Host is up (0.0030s latency).

PORT   STATE  SERVICE
21/tcp open   ftp
22/tcp closed ssh
23/tcp closed telnet
80/tcp open   http

Nmap scan report for 142.16.8.55
Host is up (0.0019s latency).

PORT   STATE  SERVICE
21/tcp open   ftp
22/tcp open   ssh
23/tcp closed telnet
80/tcp open   http

Nmap done: 32 IP addresses (32 hosts up) scanned in 324.66 seconds
```

```
IH$ proxychains nmap 142.16.8.41
Nmap scan report for 142.16.8.41
Host is up (0.0013s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
80/tcp   open  http
4567/tcp open  tram
```

## LOCAL TUNNEL 2
```
IH$ ssh net2_student12@localhost -p 21201 -L 21202:142.16.8.41:4567 -NT
```

## BILL
```
bill$ ip addr

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc pfifo_fast state UP group default qlen 1000
    link/ether fa:16:3e:95:36:cd brd ff:ff:ff:ff:ff:ff
    inet 142.16.8.41/27 brd 142.16.8.63 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::f816:3eff:fe95:36cd/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc pfifo_fast state UP group default qlen 1000
    link/ether fa:16:3e:f2:f2:a5 brd ff:ff:ff:ff:ff:ff
    inet 155.39.88.17/28 brd 155.39.88.31 scope global eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::f816:3eff:fef2:f2a5/64 scope link
       valid_lft forever preferred_lft forever
```

## NMAP SCAN BILL INTERNAL
```
IH$ proxychains nmap 155.39.88.16/28 -oN bill_int_nmap -p21-23,80

21 is up

IH$ proxychains nmap 155.39.88.21 -oN bill_int_nmap -p21-23,80

Nmap scan report for 155.39.88.21
Host is up (0.0041s latency).

PORT   STATE  SERVICE
21/tcp open   ftp
22/tcp closed ssh
23/tcp open   telnet
80/tcp open   http
```

```
IH$ proxychains wget -r http://155.39.88.21
IH$ proxychains wget -r ftp://155.39.88.21

hints.txt:
Brian's SSH port seems to be only accessible from the inside. Telnet is open to external users though. Try to tunnel to his telnet port and create a SSH remote tunnel.
```

## BILL -> BRIAN TUNNEL
```
IH$ ssh net2_student12@localhost -p 21202 -L 21203:155.39.88.21:23 -NT

IH$ telnet localhost 21203
net2_student12
password12

brian$
```

## BRIAN
```
brian$ ip addr

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc pfifo_fast state UP group default qlen 1000
    link/ether fa:16:3e:c9:d5:9b brd ff:ff:ff:ff:ff:ff
    inet 155.39.88.21/28 brd 155.39.88.31 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::f816:3eff:fec9:d59b/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc pfifo_fast state UP group default qlen 1000
    link/ether fa:16:3e:ea:5f:95 brd ff:ff:ff:ff:ff:ff
    inet 150.21.99.7/28 brd 150.21.99.15 scope global eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::f816:3eff:feea:5f95/64 scope link
       valid_lft forever preferred_lft forever
```

## BRIAN REMOTE TUNNEL
```
brian$ ssh net2_student12@155.39.88.17 -p 4567 -R 21204:localhost:22 -NT
```

## Remote Bridge
```
IH$ ssh net2_student12@localhost -p 21202 -L 21205:localhost:21204 -NT

IH$ ssh net2_student12@localhost -p 21205 -D 9050
```

# Brian Int Scan
```
IH$ proxychains nmap 150.21.99.0/28 -p21-23,80 -oN brian_int_nmap

8 is up

IH$ proxychains nmap 150.21.99.8 -p21-23,80 -oN brian_int_nmap

Nmap scan report for 150.21.99.8
Host is up (0.0042s latency).

PORT   STATE  SERVICE
21/tcp open   ftp
22/tcp closed ssh
23/tcp closed telnet
80/tcp open   http
```

```
IH$ proxychains wget -r http://150.21.99.8
IH$ proxychains wget -r ftp://150.21.99.8

hints.txt
Bob seems to have an SSH port listening above the well-known range.

IH$ proxychains nmap 150.21.99.8

Nmap scan report for 150.21.99.8
Host is up (0.0027s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
80/tcp   open  http
6789/tcp open  ibm-db2-admin
```

## BOB TUNNEL
```
ssh net2_student12@localhost -p 21205 -L 21206:150.21.99.8:6789 -NT
```
