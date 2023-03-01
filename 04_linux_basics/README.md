# 04_Linux_Basics

Start key: `start`

# Notes

## Commands, Arguments, and Help

#### Commands

Get the host version info:
```bash
uname -a
hostname -I
```

The who command gives useful info for permissions:
```bash
garviel@terra:~$ who
garviel  pts/0        2023-03-01 14:15 (10.9.0.2)
garviel@terra:~$ who -b
         system boot  2023-02-21 21:03
garviel@terra:~$ who -r
         run-level 5  2023-02-21 21:03
garviel@terra:~$ who -a
           system boot  2023-02-21 21:03
           run-level 5  2023-02-21 21:03
LOGIN      ttyS0        2023-02-25 06:44             11642 id=tyS0
LOGIN      tty1         2023-02-21 21:03              1044 id=tty1
garviel  + pts/0        2023-03-01 14:15   .         25517 (10.9.0.2)
           pts/1        2023-03-01 14:27             25746 id=ts/1  term=0 exit=0
```

The `ip` command:
```bash
garviel@terra:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000        
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ens3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc fq_codel state UP group default qlen 1000
    link/ether fa:16:3e:31:3f:72 brd ff:ff:ff:ff:ff:ff
    inet 10.9.0.6/24 brd 10.9.0.255 scope global dynamic ens3
       valid_lft 58242sec preferred_lft 58242sec
    inet6 fe80::f816:3eff:fe31:3f72/64 scope link
       valid_lft forever preferred_lft forever
```

Neighbor discovery
```bash
garviel@terra:~$ ip neigh
10.9.0.201 dev ens3 lladdr fa:16:3e:24:2f:83 STALE  
10.9.0.2 dev ens3 lladdr fa:16:3e:6f:d9:07 REACHABLE
10.9.0.200 dev ens3 lladdr fa:16:3e:6d:1a:b4 STALE  
10.9.0.254 dev ens3 lladdr fa:16:3e:64:5d:53 STALE  
garviel@terra:~$ arp -a
? (10.9.0.201) at fa:16:3e:24:2f:83 [ether] on ens3
? (10.9.0.2) at fa:16:3e:6f:d9:07 [ether] on ens3  
? (10.9.0.200) at fa:16:3e:6d:1a:b4 [ether] on ens3       
_gateway (10.9.0.254) at fa:16:3e:64:5d:53 [ether] on ens3
```
