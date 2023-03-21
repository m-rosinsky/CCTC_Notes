# BPF Filtering

# Well-Known Ports
```
tcp[2:2]<1024||udp[2:2]<1024
```

# HTTP
```
tcp[0:2]=80||tcp[2:2]=80
```

# Telnet
```
tcp[0:2]=23||tcp[2:2]=23
```

# ARP
```
ether[12:2]=0x0806
```

# Evil Bit
```
ip[6]&128=128
```

# Chaos
```
ip[9]=16
```

# DSCP
```
ip[1]>>2=37
```

# Traceroute
```
ip[8]=1&&(ip[9]=1||ip[9]=17)
```

# URGent
```
tcp[13]&32=0&&tcp[18:2]!=0
```

# NULL SCAN
```
ip[16:4]=0x0A0A0A0A&&tcp[13]=0
```
