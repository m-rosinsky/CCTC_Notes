# Scanning Notes

## OSINT

Gathering open source data.

## Scraping Data

Python requests.

From lin-ops station:
```
quotes.toscrape.com
```

```python
#!/usr/bin/python
import lxml.html
import requests

page = requests.get('http://quotes.toscrape.com')
tree = lxml.html.fromstring(page.content)

authors = tree.xpath('//small[@class="author"]/text()')

print('Authors: ', authors)
```

## Advanced Scanning Techniques

1. Host Discovery
    - Find the hosts that are online
2. Port enumeration
    - Find open ports on a host
3. Port interrogation
    - Find services running on open ports

## Host Discovery

Dynamic tunnel to jumpbox from lin-ops
```bash
for i in {2..254} ; do (ping -c 1 192.168.28.$i | grep "bytes from" &) ; done
```

```
64 bytes from 192.168.28.2: icmp_seq=1 ttl=63 time=1.63 ms
64 bytes from 192.168.28.3: icmp_seq=1 ttl=63 time=1.25 ms
64 bytes from 192.168.28.97: icmp_seq=1 ttl=64 time=0.548 ms
64 bytes from 192.168.28.98: icmp_seq=1 ttl=63 time=2.70 ms
64 bytes from 192.168.28.99: icmp_seq=1 ttl=63 time=3.58 ms
64 bytes from 192.168.28.100: icmp_seq=1 ttl=63 time=1.70 ms
64 bytes from 192.168.28.105: icmp_seq=1 ttl=63 time=1.52 ms
64 bytes from 192.168.28.111: icmp_seq=1 ttl=63 time=1.46 ms
64 bytes from 192.168.28.120: icmp_seq=1 ttl=63 time=1.35 ms
64 bytes from 192.168.28.129: icmp_seq=1 ttl=64 time=0.707 ms
64 bytes from 192.168.28.130: icmp_seq=1 ttl=63 time=2.92 ms
64 bytes from 192.168.28.131: icmp_seq=1 ttl=63 time=1.71 ms
```

## Port Enumeration

Proxychains nmap scan:
(ipz contains list of all ips from above scan)
```
proxychains nmap -iL ipz -sT -Pn -T5 -p 80 --open
```

```
Nmap scan report for 192.168.28.111
Host is up (0.0033s latency).

PORT   STATE SERVICE
80/tcp open  http

Nmap done: 12 IP addresses (12 hosts up) scanned in 0.07 seconds
```

Proxychains full report:
```
proxychains nmap -iL ipz -sT -Pn -T5 --open
```

```
Nmap scan report for 192.168.28.100
Host is up (0.0016s latency).
Not shown: 999 closed ports
PORT     STATE SERVICE
2222/tcp open  EtherNetIP-1

Nmap scan report for 192.168.28.105
Host is up (0.0017s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
2222/tcp open  EtherNetIP-1

Nmap scan report for 192.168.28.111
Host is up (0.0017s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE
80/tcp   open  http
2222/tcp open  EtherNetIP-1
8080/tcp open  http-proxy

Nmap scan report for 192.168.28.120
Host is up (0.0017s latency).
Not shown: 999 closed ports
PORT     STATE SERVICE
4242/tcp open  vrml-multi-use
```

## Port Interrogation

- using firefox for web servers (with proxy)
- nc (via proxy) for banner grabbing others

192.168.28.10:
```
4242 - SSH
```

# NMAP Scripting Engine

Script location:
```
/usr/share/nmap/scripts/
```

Recommended Scripts:
```
http-enum.nse
```

```
proxychains nmap --script http-enum 192.168.28.111 -p 80 -sT -Pn -T5
```

```
Nmap scan report for 192.168.28.111
Host is up (0.0033s latency).

PORT   STATE SERVICE
80/tcp open  http
| http-enum:
|   /css/: Potentially interesting directory w/ listing on 'apache/2.4.29 (ubuntu)'
|   /images/: Potentially interesting directory w/ listing on 'apache/2.4.29 (ubuntu)'
|_  /sites/: Potentially interesting folder
```

SMB:
```
smb-os-discovery.nse
```
