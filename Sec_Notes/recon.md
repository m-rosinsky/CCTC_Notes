# Operation Golden Nugget

Scheme of Movement:
```
>Jump
->192.168.28.96/27
-->192.168.150.224/27

OSs: Unknown
Creds: student ::
Known Ports: Unknown
Known URL: consulting.site.donovia
Known URL: conference.site.donovia
```

## FTP (5)

- Dynamic tunnel from jump
- `wget` FTP from 192.168.28.105
```
$ cat ServerInitialization
PassTemporary
loginfirst
logout null bit
houseBeatFliesLOW
YourTempPassword

okE9u0OvfAh7JAuwPBNm
```

## Key Speaker

192.168.28.111:8080 -> BPKSlKYF9gCpNegzl41j

## Strong tags

Enumerate website:
```
Nmap scan report for 192.168.28.111
Host is up (0.0026s latency).

PORT     STATE SERVICE
8080/tcp open  http-proxy
| http-enum:
|   /css/: Potentially interesting directory w/ listing on 'apache/2.4.29 (ubuntu)'
|   /images/: Potentially interesting directory w/ listing on 'apache/2.4.29 (ubuntu)'
|_  /js/: Potentially interesting directory w/ listing on 'apache/2.4.29 (ubuntu)'
```

wRboVtIXFQ7lCJuGtngi

/news.html
TXZvsecEkoNTqFqHiQU4

## Contact Info

/sites/NSC-Contact.html
```
h8kvI
Mnjmp
QwkkE
oasMo

h8kvIMnjmpQwkkEoasMo
```

## Company Article

/sites
```
<dd class="org-title"></dd>
```
YagDiaWB6wV42BXOStE3

## SMB

YourTempPassword

Ping Sweep:
```
192.168.150.225
192.168.150.226
192.168.150.227
192.168.150.245
```

Scan of .245:
```
Nmap scan report for 192.168.150.245
Host is up (0.0018s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3389/tcp open  ms-wbt-server
9999/tcp open  abyss

Host script results:
| smb-os-discovery:
|   OS: Windows 10 Enterprise 17134 (Windows 10 Enterprise 6.3)
|   OS CPE: cpe:/o:microsoft:windows_10::-
|   Computer name: 30CiG5yQvDlKCxAdXkzn
|   NetBIOS computer name: 30CIG5YQVDLKCXA\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2023-04-06T18:21:39+00:00
```
