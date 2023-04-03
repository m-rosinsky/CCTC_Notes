# CCTC Networking Capstone Notes

Convert all answers to `base64`

Start Pivot 1 IP: 10.50.32.253

Common shared folder: `/usr/share/cctc/`

# Web Questions

NMAP Pivot 1:
22 - SSH
80 - HTTP (nginx)

`wget -r http://$IP`

hint-01a.png

`ip addr`:
10.1.1.30/25

`ip nei`:
10.1.1.11 dev eth0 lladdr fa:16:3e:b4:6b:c1 REACHABLE
10.1.1.25 dev eth0 lladdr fa:16:3e:42:5b:35 REACHABLE
10.1.1.33 dev eth0 lladdr fa:16:3e:04:14:87 REACHABLE
10.1.1.126 dev eth0 lladdr fa:16:3e:37:22:64 REACHABLE
10.1.1.125 dev eth0 lladdr fa:16:3e:d5:72:80 STALE

Up:
```
.11, .25, .33, .125
```

.11 WGET:
```
hint-02a.png -> Webservice running on port corresponds with RFC that
                governs Private IPv4 Addressing (1918)
hint-02b.png -> There is a PCAP saved in the share folder of this machine
                that you should look at.
```

.11 High Port:
```
1918 -> HTTP
```

Wget 10.1.1.11:1918:
```
index-1.html:
APIPA uses the IP network range of 169.254.0.0/16. What RFC number governs this? Enter only the BASE64 conversion of the number.

3927 -> MzkyNwo=

index-2.html:
IPv6 Uses SLAAC to resolve its Global address from the Router. What multicast destination address does it use to Solicit the router?
Enter the address in uppercase and convert to BASE64.

FF02::2 -> RkYwMjo6Mgo=

index-3.html:
Which type of ARP is sent in order to perform a MitM attack?
Specify the answer in ALL CAPS and convert to BASE64.

GRATUITOUS -> R1JBVFVJVE9VUwo=

index-4.html:
An attacker built a FRAME that looks like this:</p>
| Destination MAC | Source MAC | 0x8100 | 1 | 0x8100 | 100 | 0x0800 | IPv4 Header | TCP Header | Data | FCS |
What form of attack is being performed? Supply your answer in ALL CAPS and convert to BASE64.

VLAN HOPPING -> VkxBTiBIT1BQSU5HCg==

index-5.html
A router receives a 5000 byte packet on eth0. The MTU for the outbound interface (eth1) is 1500. What would the fragmentation offset increment be with the conditions below?
Origional packet Size = 5000 bytes
MTU for outboud interface = 1500
Packet IHL = 7
Supply only the BASE64 conversion of the number.

184 -> MTg0Cg==
```

.11 Tunnel:
```
Tunnel on 21201 to telnet 10.1.1.11
```

## PCAP Questions

.11 Telnet:
```
capstone-02$ cd /usr/share/cctc
cat Flag-02f.txt

To answer these 4 questions, you will need to use tcpdump and BPF's against the capstone-bpf.pcap file.


-------------------------------------------------------------------------------

Question 1:

Using BPF’s, determine how many packets with a DSCP of 26 being sent to the host 10.0.0.103.

Provide the number of packets converted to BASE64.

Answer 1:
tcpdump -r capstone-bpf.pcap "ip[1]>>2=26&&ip[16:4]=0x0a000067" | wc -l
108 -> MTA4Cg==

-------------------------------------------------------------------------------

Question 2:

What is the total number of fragmented packets?

Provide the number of packets converted to BASE64.

Answer 2:
tcpdump -r capstone-bpf.pcap "ip[6]&32=32" | wc -l
2160 + 569 -> 2729 -> MjcyOQo=

-------------------------------------------------------------------------------

Question 3:

How many packets have the DF flag set and has ONLY the RST and FIN TCP Flags set?

Provide the number of packets converted to BASE64.

Answer 3:
tcpdump -r capstone-bpf.pcap "ip[6]&64=64&&tcp[13]=0x5" | wc -l
109 -> MTA5Cg==

-------------------------------------------------------------------------------

Question 4:

An attacker is targeting the host 10.0.0.104 with either a TCP full or half open scan. Based off the pcap, how many ports are open?

Provide the number of ports converted to BASE64.

Answer 4:
tcpdump -r capstone-bpf.pcap "ip[12:4]=0x0a000068&&tcp[13]&16=16&&tcp[13]&2=2" | wc -l
18 -> MTgK

-------------------------------------------------------------------------------
```

## 03 Web Questions

WGET 10.1.1.25
```
hint-03a.png -> Web service running on port RFC IPv4 Header structure (791)
hint-03b.png -> TCP port listening.
                Connect and say hi.
                Decode response for flag.
```

WGET 10.1.1.25:791
```
index-1.html

RAW Sockets are created in ________ space. Specify the one word BASE64 conversion of your answer in ALL CAPS.

KERNEL -> S0VSTkVMCg==
```

```
index-2.html

Which module would you need to import to convert data into a corresponding 2-digit hex representation?
Specify the module in lowercase and converted to BASE64.

binascii -> YmluYXNjaWkK
```

```
index-3.html

What is the proper format to pro-grammatically pack the IPv4 RAW header?
Specify the answer in the proper case. Include only what is between the single or double quotes and not the quotes themselves or the “!”.
Provide the answer converted to BASE64.

BBHHHBBH4s4s -> QkJISEhCQkg0czRzCg==
```

```
index-4.html

What is the default (and most common) encoding used when converting data to be sent over the network. Provide your answer in ALL CAPS and converted to BASE64.

UTF-8 -> VVRGLTgK
```

```
index-5.html

What type of header does TCP build to perform the checksum function?
i.e. [ANSWER] Header
Provide your answer in ALL CAPS and converted to BASE64.

PSEUDO -> UFNFVURPCg==
```

Socket Crafting:
```
TCP Port: 4869

Bazinga -> QmF6aW5nYQo=
```

## Malware Discovery

WGET 10.1.1.33
```
hint-04a.png -> Another box (capstone-05) that only this box can see.
                That box is attacking this box on port associated with W32/Blaster Worm.
                Use sniffing tool to try to find the message.

tcpdump -i eth1 -c 5 -nvvvX
I just want to say LOVE YOU SAN

SSBqdXN0IHdhbnQgdG8gc2F5IExPVkUgWU9VIFNBTgo=
```

```
hint-04b.png -> RIPv2 running on 10.1.1.0/25 network.
                Sniff traffic to find what networks it is advertising.
                Will be your next pivot.

RIP Port: 520

Next Pivot:
10.50.26.110
```

# 06 Port Discovery

WGET 10.50.26.110:
```
hint-06a.png -> SSH running on higher port.
                Only accepts conns coming from a Cisco Device's TTL.
                Use iptables to adjust sending TTL.
                Flag is SSH port number.

iptables -t mangle -A POSTROUTING -j TTL --ttl-set 255

7777 -> Nzc3Nwo=
```

SSH into 10.50.26.110
```
ip addr

eth0: 10.2.2.6/28
```

Scan 10.2.2.0/28:
```
Up: 10.2.2.7
```

WGET 10.2.2.7:
```
hint-07a.png -> SSH running on higher port. Not accessible from outside.
                Different credentials.
                Intercept creds?
                Another system has tool that can help us.
                Flag is password converted to base64.
                Creds will be exactly what you find.
```

10.2.2.7 SSH Creds
```
06$ tcpdump -nvvvX -i eth0 "ip[12:4]=0x0a020207"

Password: Netflix and Chill
```

Telnet 10.2.2.7 (Reverse Tunnel)
```
Up: 10.10.10.140
```

## 08 Port Discovery

WGET 10.10.10.140:
```
hint-08a.png -> SSH running on port 301
                Flag is port number converted to base64.

                301 -> MzAxCg==
```

## 09 Net recon

Tunnel from 08 -> 09
```
Found 192.168.10.32/27 net
```

Scan 192.168.10.39:
```
21, 4444
4444 -> So, is Metasploit a good thing or a bad thing for security?
```

WGET 192.168.10.30:
```
21 -> hints
3790 -> index files
```

index-1.html:
```
What type of recon is being performed if you are performing ARP scans and sending Gratuitous ARPs to perform a MitM attack?
Provide the 2 word process in ALL CAPS and converted to Base64.
i.e. [word1] [word2]

INTERNAL ACTIVE -> SU5URVJOQUwgQUNUSVZFCg==
```

index-2.html:
```
What is the typical flag response (if any) would a Linux host perform when receiving a Stealth scan on an CLOSED port?
Provide the 3 letter abbreviated name of the FLAG(s) in ALL CAPS, separated by / (use “NONE” if no response) and converted to Base64.

RST -> UlNUCg==
```

index-3.html
```
What command line tool can be used to pull DNS information from the server using TCP port 43?
Provide the command in ALL CAPS and converted to Base64.

WHOIS -> V0hPSVMK
```

index-4.html
```
Which NMAP scan is able to determine open ports on a target without actually communicating with it?
Provide the scan name in ALL CAPS and converted to Base64.

IDLE -> SURMRQo=
```

index-5.html
```
A cyber analyst wants to us Netcat to perform a banner grab on a target IP of 10.1.0.1 port 1111.
Provide the exact command (without switches and including spaces) you would perform on the command line and converted to Base64.

nc 10.1.0.1 1111 -> bmMgMTAuMS4wLjEgMTExMQo=
```

## 10 Port Discovery

Capstone 10: 10.10.10.167:
```
hint-10a.png -> SSH running on port 404

404 -> NDA0Cg==

hint-10b.png -> This system is pivot for Movement and Redir section.
```

## Movement and Redirection

Scan Cap 10:
```
Up: 192.168.10.80
21, 9050
```

index-1.html:
```
D -> RAo=
```

index-2.html
```
B -> QQo=
```

index-3.html
```
ASYMMETRIC -> QVNZTU1FVFJJQwo=
```

index-4.html
```
proxychains scp tgt@192.168.1.10:secret.txt .
->
cHJveHljaGFpbnMgc2NwIHRndEAxOTIuMTY4LjEuMTA6c2VjcmV0LnR4dCAuCg==
```

index-5.html
```
SFTP -> U0ZUUAo=
```

## 12 Port Discovery

WGET 10.10.10.182:
```
hint-12a.png -> SSH on port for HTTP status code for Gateway Timeout

504 ->
```

## 13

IP: 192.168.10.101

WGET:
```
hint-13a.png -> Web service on um of 2 ports for SMB WannaCry Ransomware.
                (584)
```

index-1.html:
```
CONVERSATIONS -> Q09OVkVSU0FUSU9OUwo=
```

index-2.html:
```
NETFLOW -> TkVURkxPVwo=
```

index-3.html:
```
TAP -> VEFQCg==
```

index-4.html:
```
COMPROMISE -> Q09NUFJPTUlTRQo=
```

index-5.html:
```
METAMORPHIC -> TUVUQU1PUlBISUMK
```

PCAP:

To answer these 8 questions, you will need extract the capstone-analysis.pcap file and open it with Wireshark.

-------------------------------------------------------------------------------

Question 1:

Which ip address initiated the attack against the FTP server?

Provide the ip address in the x.x.x.x format and converted to Base64.

Answer 1:
10.1.0.108 -> MTAuMS4wLjEwOAo=

-------------------------------------------------------------------------------

Question 2:

How many failed attempts to guess the FTP password?

Provide number and converted to Base64.

Answer 2:
4 -> NAo=

-------------------------------------------------------------------------------

Question 3:

What is the correct FTP password?

Provide the exact password and converted to Base64.

Answer:
w -> dwo=

-------------------------------------------------------------------------------

Question 4:

What is the system IP that was compromised?

Provide the ip address in the x.x.x.x format and converted to Base64.

Answer:
10.2.0.2 -> MTAuMi4wLjIK

-------------------------------------------------------------------------------

Question 5:

What is the FTP version?

Provide the version number only and converted to Base64.

Answer:
3.0.2 -> My4wLjIK

-------------------------------------------------------------------------------

Question 6:

What is the name of the file taken by the attacker?

Provide the filename exactly as shown and converted to Base64.

Answer:
test.txt -> dGVzdC50eHQK

-------------------------------------------------------------------------------

Question 7:

What was the message contained within the extracted file?

Provide the message exactly as shown and converted to Base64.

Answer:
hi -> aGkK

-------------------------------------------------------------------------------

Question 8:

What is the name of the file uploaded by the attacker?

Provide the filename exactly as shown and converted to Base64.

Answer:
company_payroll_2019 -> Y29tcGFueV9wYXlyb2xsXzIwMTkK

-------------------------------------------------------------------------------

## 14

IP: 192.168.10.111

NMAP:
```
Nmap scan report for 192.168.10.111
Host is up (0.0014s latency).
Not shown: 9989 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
88/tcp   open  kerberos-sec
123/tcp  open  ntp
357/tcp  open  bhevent
791/tcp  open  unknown
859/tcp  open  unknown
1321/tcp open  pip
1999/tcp open  tcp-id-port
2223/tcp open  rockwell-csp2
2711/tcp open  sso-control
```

WGET:
```
hint-14a.png -> Webservice running on Expanded Extended Cisco Numbered ACL Range.
                (2223)
hint-14b.png -> Snort is running on this machine. Look through its file locations.
```

WGET 2223:
```
index questions
```

index-1.html:
```
In NAT, which Hook would I place a rule to change the source IP for all traffic thru this host?
Specify your 1 word answer in ALL CAPS and converted to Base64.

Answer:
POSTROUTING -> UE9TVFJPVVRJTkcK
```

index-2.html:
```
Which Hook would I apply rules that are destined for the ‘localhost’?
Specify your 1 word answer in ALL CAPS and converted to Base64.

Answer:
INPUT -> SU5QVVQK
```

index-3.html:
```
What recognition method do IDS/IPS primarily use to detect malicious traffic?
Specify your 1 word answer in ALL CAPS and converted to Base64.

Answer:
SIGNATURE -> U0lHTkFUVVJFCg==
```

index-4.html:
```
In iptables, which Table would I use if I wanted to preform packet alterations?
Specify your 1 word answer in ALL CAPS and converted to Base64.

Answer:
MANGLE -> TUFOR0xFCg==
```

index-5.html:
```
What is the default family for NFTables?
Specify your 1 word answer in ALL CAPS and converted to Base64.

Answer:
IP -> SVAK
```

Flag-14f.txt:
```
To answer these s questions, you will need to examine the Snort services running on this system.


-------------------------------------------------------------------------------

Question 1:

How many rule files are on the system?

Provide the number converted to Base64 as your answer.

Answer:
24 -> MjQK

-------------------------------------------------------------------------------

Question 2:

How many of the rules are being used to match for traffic?

Provide the number converted to Base64 as your answer.

Answer:
7 -> Nwo=

-------------------------------------------------------------------------------

Question 3:

Which rule will look for someone doing a null scan ?

Provide only the filename as your answer (i.e. ‘file.rules’) and converted to Base64.

Answer:
alien-abductions.rules -> YWxpZW4tYWJkdWN0aW9ucy5ydWxlcwo=

-------------------------------------------------------------------------------

Question 4:

What is the exact Alert Message that is being triggered on the system?

Convert the exact message as you see it and convert it to Base64 for your answer.

Answer:
ps -elf -all | grep snort
cat alert

Who got that kinda monies to pay that! ->
V2hvIGdvdCB0aGF0IGtpbmRhIG1vbmllcyB0byBwYXkgdGhhdCEK

---------------------------------------------------------------

Question 5:

From what IP is the attack coming from?

Provide your answer in the x.x.x.x format and converted to Base64.

Answer:
192.168.10.99 -> 
MTkyLjE2OC4xMC45OQo=

-------------------------------------------------------------------------------

```
