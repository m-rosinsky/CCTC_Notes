# CMT Operator Notes

## Credentials
```
administrator:pokemon  (used on DMZ Web Server login page)
brett:Venezuela        (used on DMZ FTP server)
nelmanso:password
raljabar:123456
teljalal:00000         (used on DMZ Web Server ssh login)
malmowad:181991        (used on Ground 57)
relsalih:Password123   (used on Air 105)
jjaheer:phillip22
jackasis:SuperSecure1
```

## Edge Router
OS:
```
Linux (Likely VyOS but confirmed)
```

Hostname:
Not Found

IP:
```
10.50.34.115 (External)
```

Ports:
- 22 SSH (Forwards to 172.17.7.21)
- 21 FTP (Forwards to 172.17.7.21)
- 80 HTTP (Forwards to 172.17.7.80)
- 8080 HTTP (Forwards to 172.17.7.80)

Credentials:
None

---

## Web Server (DMZ)
OS:
```
Linux, running Apache 2.4.25
```

Hostname:
```
donovia-mil-dmz-80-d9l
```

IP:
```
172.17.7.80 (Internal)
10.50.34.115:80 (Port forward from Edge Router)
10.50.34.115:8080 (Port forward from Edge Router)
```

Ports:
- 22 SSH (Made by reverse tunnel. If tunnel is taken down, this may not be open)
- 80 HTTP
- 8080 HTTP Alt

Credentials:
- administrator:pokemon (on http://172.17.7.80:8080/admin)
- teljalal:00000 (ssh, in /etc/sudoers for ALL commands)
- root:toor (cannot ssh, but can use to priv esc once already in)

HTTP-Enum:
```
80/tcp   open  http	nginx 1.10.3
|_http-server-header: nginx/1.10.3
8080/tcp open  http	Apache httpd 2.4.25 ((Debian))
| http-enum:
|   /admin/: Possible admin folder
|   /admin/index.php: Possible admin folder
|   /backups/: Backup folder w/ directory listing
|   /robots.txt: Robots file
```

## FTP Server (DMZ)
OS:
```
Linux, running vsftpd 3.0.3 for FTP
```

Hostname:
Not Found

IP:
```
172.17.7.21 (Internal)
```

Ports:
- 21 FTP
- 22 SSH

Credentials:
- Not Tested, wget was able to grab files without credentials.
- SSH not tried

Files Grabbed:
```
donovia_network.png
```

## Domain Controller (DC Enclave)
OS:
```
Windows (Need Version)
```

Hostname:
```
DONOVIA-MIL-DC0
```

IP:
```
172.17.6.50 (Internal)
```

Ports:
- 22 SSH

Credentials:
- teljalal:00000 (via SSH)

## Ground 57 (Ground Enclave)
OS:
```
Linux
```

Hostname:
```
donovia-mil-ground-57-d9l
```

IP:
```
172.17.3.57 (Internal)
```

Ports:
- 22 SSH

Credentials:
- malmowad:181991 (via SSH)

## Air 105 (Air Enclave)
OS:
```
Linux
```

Hostname:
```
donovia-mil-air-105-d9l
```

IP:
```
172.17.4.105 (Internal, eth0)
192.168.38.129 (Internal, tun0)
```

Ports:
- 22 SSH
- 3781 Unknown

Credentials:
- relsalih:Password123 (via SSH)
- root:toor (No SSH, but for priv esc once already in)

## Naval 88 (Naval Enclave)
OS:
Not Found

Hostname:
Not Found

IP:
```
172.17.2.88 (Internal)
```

Ports:
- 22 SSH

Credentials:
None Found

## Air Defense Controller (Air Enclave Internal)
OS:
Not Found

Hostname:
Not Found

IP:
```
192.168.38.130 (Internal, visible from tun0 on Air 105)
```

Ports:
- 1090 ff-fms
- 30001
- 30002
- 30003
- 30004
- 30005

Credentials:
None Found, no open SSH ports.

## Government Router
OS:
```
VyOS
```

Hostname:
```
host-router
```

IP:
```
172.18.1.40 (Internal)
```

Ports:
- 22 SSH

Credentials:
- sarred:sarred (via SSH)

Interfaces:
```
eth0         	172.18.1.40/24                	u/u  ROUTER_NETWORK
eth1         	172.18.2.1/24                 	u/u  INTERIOR NETWORK
eth2         	172.18.3.1/24                 	u/u  GOV_TRANSPO
eth3         	172.18.4.1/24                 	u/u  GOV_FINANCE
eth4         	172.18.5.1/24                 	u/u  GOV_LEADERSHIP
eth5         	172.18.6.1/24                 	u/u  GOV_DC
eth6         	172.18.7.1/24                 	u/u  GOV_DMZ
eth7         	172.18.8.1/24                 	u/u  GOV_INTEL
eth8         	172.18.10.1/24                	u/u  GOV_SECONION
lo           	127.0.0.1/8                   	u/u  LAN_RTR_LO
             	172.0.0.3/32
             	::1/128
```

## Government Web Server (Gov DMZ)
OS:
```
Linux
```

Hostname:
```
donovia-gov-dmz-80-u14l
```

IP:
```
172.18.7.80 (Internal)
```

Ports:
- 21 FTP
- 22 SSH
- 80 HTTP

Credentials:
- nelmanso:password (via SSH)

## Gov Interior 234
OS:
```

```

Hostname:
```

```

IP:
```
172.18.2.234
```

Ports:
- 80 HTTP

Credentials:


## Government Interior 199
OS:
```

```

Hostname:
```

```

IP:
```
172.18.2.199
```

Ports:
- 22 SSH

Credentials:

## Government Interior 26
OS:
```

```

Hostname:
```

```

IP:
```
172.18.2.26
```

Ports:
- 22 SSH

Credentials:

## Government Interior 102
OS:
```

```

Hostname:
```

```

IP:
```
172.18.2.102
```

Ports:
- 21 FTP
- 22 SSH
- 23 Telnet
- 25 SMTP
- 139 SMB
- 445 SMB
- 3389 RDP
- 8080 HTTP Alt

Credentials:

## Government Transpo 10
OS:
```

```

Hostname:
```

```

IP:
```
172.18.3.10
```

Ports:
- 22 SSH

Credentials:

## Government Transpo 21
OS:
```

```

Hostname:
```

```

IP:
```
172.18.3.21
```

Ports:
- 22 SSH

Credentials:

## Government Transpo 66
OS:
```

```

Hostname:
```

```

IP:
```
172.18.3.66
```

Ports:
- 22 SSH

Credentials:

## Government Transpo 95
OS:
```

```

Hostname:
```

```

IP:
```
172.18.3.95
```

Ports:
- 8080 HTTP Alt

Credentials:
