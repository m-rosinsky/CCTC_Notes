# Network Fundamentals

# 1. (5)
Prompt:
```
What MAC address is initiating the ARP Storm?
```

```
00:07:0d:af:f4:54
```

# 2. (5)
Prompt:
```
What is the MAC of 10.10.10.1?
```

```
00:1d:09:f0:92:ab
```

# 3. (5)
Prompt:
```
What is the MAC of 10.10.10.2?
```

```
00:1a:6b:6c:0c:cc
```

# 4. (5)
Prompt:
```
What is the MAC address of the system trying to perform the ARP MitM attack?
```

```
fa:16:3e:35:21:5a
```

# 5. (5)
Prompt:
```
What is the OP code of a RARP Request?
```

```
3
```

# 6. (5)
Prompt:
```
What is the OP code of a RARP Response?
```

```
4
```

# 7. (5)
Prompt:
```
What is the RARP requestor’s MAC?
```

```
arp.opcode == 3
```

```
00:0c:29:34:0b:de
```

# 8. (5)
Prompt:
```
What was the RARP requestor’s resolved IP address?
```

```
eth.dst == 00:0c:29:34:0b:de
```

```
10.1.1.100
```

# 9. (5)
Prompt:
```
What is the MAC of the system spamming gratuitous ARP’s for 192.168.1.254?
```

```
arp.opcode == 2
```

```
00:00:5e:00:01:01
```

# 10. (5)
Prompt:
```
What is the software version of the Cisco Switch (copy entire field “as is” from Wireshark)?
```

```
IOS (tm) C2950 Software (C2950-I6K2L2Q4-M), Version 12.1(22)EA14, RELEASE SOFTWARE (fc1)
```

# 11. (5)
Prompt:
```
What is the software version of the Cisco Router (copy entire field “as is” from Wireshark)?
```

```
IOS (tm) 1600 Software (C1600-NY-L), Version 11.2(12)P, RELEASE SOFTWARE (fc1)
```

# 12. (5)
Prompt:
```
What is the System Name of one of the LLDP sending devices?
```

```
S2.cisco.com
```

# 13. (5)
Prompt:
```
What is the Bridge Priority of the STP Root Bridge?
```

```
0
```

# 14. (5)
Prompt:
```
What is the MAC address of the STP Root Bridge?
```

```
00:1f:27:b4:7d:80
```

# 15. (5)
Prompt:
```
What is the VTP Management Domain Name?
```

```
cisco
```

# 16. (5)
Prompt:
```
What is the latest configuration revision number?
```

```
11
```

# 17. (5)
Prompt:
```
How many total VLANs are being advertised via VTP?
```

```
22
```

# 18. (5)
Prompt:
```
What is the message contained within the single tagged VLAN traffic coming from 11.22.33.44?
```

```
ip.src == 11.22.33.44
```

```
i pitty the foo
```

# 19. (5)
Prompt:
```
What is the VLAN ID of this traffic?
```

```
999
```

# 20. (5)
Prompt:
```
What is the VLAN ID being attacked by 10.10.10.10 using Double Tagging?
```

```
ip.src == 10.10.10.10
```

```
250
```

# 21. (5)
Prompt:
```
What is the combined message begin sent via ICMP?
```

```
Wouldn't you like too be a Pepper Too!
```

# 22. (5)
Prompt:
```
What is the OS of 192.168.1.1 host based off its Echo Request message to the Google DNS?
```

```
Linux
```

# 23. (5)
Prompt:
```
What is the message that 192.168.65.20 sending to Google's DNS via ICMP?
```

```
Exsqueeze me?
```

# 24. (5)
Prompt:
```
How many Hops away is the 151.101.64.84 address?
```

```
11
```

# 25. (5)
Prompt:
```
What is the IP ID of the fragmented ICMP packet? (starting at packet 6472)
```

```
46544
```

# 26. (5)
Prompt:
```
What is the offset value of the fragments?

    Not the calculated value shown in Wireshark

    Suggest converting the value from the Hex Dump
```

```
122
```

# 27. (5)
Prompt:
```
What is the possible OS of the system that sent this ICMP based on the message payload?
```

```
windows
```

# 28. (5)
Prompt:
```
What is the ICMPv6 type number of Echo Request?
```

```
128
```

# 29. (5)
Prompt:
```
What is the ICMPv6 type number of Echo Reply?
```

```
129
```

# 30. (5)
Prompt:
```
What is the ICMPv6 type number of the Router Advertisement message?
```

```
134
```

# 31. (5)
Prompt:
```
What is the link-layer address of the advertising router?
```

```
fa:16:3e:35:21:5a
```

# 32. (5)
Prompt:
```
What is the IPv6 prefix being advertised?
```

```
beef:4:f00d::
```

# 33. (5)
Prompt:
```
What is the HSRP virtual IP?
```

```
192.168.0.1
```

# 34. (5)
Prompt:
```
What the the HSRP multicast address used?
```

```
224.0.0.2
```

# 35. (5)
Prompt:
```
What is the IP address of the HSRP Active forwarder (before the takeover)?
```

```
192.168.0.30
```

# 36. (5)
Prompt:
```
What is the IP address of the HSRP Active forwarder (after the takeover)?
```

```
192.168.0.10
```

# 37. (5)
Prompt:
```
What is the VRRP multicast address used?
```

```
224.0.0.18
```

# 38. (5)
Prompt:
```
What is the VRRP virtual IP?
```

```
192.168.1.254
```

# 39. (5)
Prompt:
```
How many total devices are communicating via VRRP?
```

```
3
```

# 40. (5)
Prompt:
```
How many total devices are communicating via VRRP?
```

```
2
```

# 41. (5)
Prompt:
```
What are the networks being advertised (in numeric order separated by commas and no spaces)?
```

```
200.0.1.0,200.0.2.0
```

# 42. (5)
Prompt:
```
What Protocol and port is being used for RIP?

Transport PROTOCOL PORT
```

```
udp 520
```

# 43. (5)
Prompt:
```
What network is being advertised via EIGRPv4
```

```
192.168.4.0
```

# 44. (5)
Prompt:
```
What is the IP protocol number used for EIGRP?
```

```
88
```

# 45. (5)
Prompt:
```
What multicast address is used to send EIGRPv4 updates?
```

```
224.0.0.10
```

# 46. (5)
Prompt:
```
What network is being advertised via EIGRPv6
```

```
2001:db8:0:400::
```

# 47. (5)
Prompt:
```
What multicast address is used to send EIGRPv6 updates?
```

```
ff02::a
```

# 48. (5)
Prompt:
```
What Autonomous system number is being used?
```

```
100
```

# 49. (5)
Prompt:
```
What is the IP protocol number used for OSPF?
```

```
89
```

# 50. (5)
Prompt:
```
What is the IP address of the OSPF designated router (DR)?
```

```
192.168.170.8
```

# 51. (5)
Prompt:
```
What multicast address is used by the DR to send updates?
```

```
224.0.0.5
```

# 52. (5)
Prompt:
```
How many networks are being advertised via BGP?
```

```
3
```

# 53. (5)
Prompt:
```
How many networks are being advertised via BGP?
```

```
10.0.0.0,172.16.0.0,192.168.4.0
```

# 54. (5)
Prompt:
```
What Autonomous system number is the 192.168.0.10 peer in?
```

```
65210
```

# 55. (5)
Prompt:
```
What Protocol and port is being used for BGP?
```

```
tcp 179
```
