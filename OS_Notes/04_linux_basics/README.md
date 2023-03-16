# 04_Linux_Basics

Start key: `start5309`

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

#### Variables and Command Substitution

```bash
$ a=100
$ echo $a
100

$ unset $a
```

## Scripting

#### For Loops

```bash
garviel@terra:~$ for i in {1..5}
> do
> echo "Welcome $i times"
> done
Welcome 1 times  
Welcome 2 times  
Welcome 3 times  
Welcome 4 times  
Welcome 5 times
```

```bash
garviel@terra:~$ for i in $dirs
> do
> echo $i
> done
/etc/NetworkManager
/etc/X11
/etc/acpi
/etc/adduser.conf
/etc/alternatives
/etc/apache2
/etc/apm
```

```bash
garviel@terra:~$ for i in $dirs
> do
> if [ -d $i ] ;
> then
> echo "$i is a dir"
> else
> echo "$i is a file"
> fi
> done
/etc/NetworkManager is a dir
/etc/X11 is a dir
/etc/acpi is a dir
/etc/adduser.conf is a file
/etc/alternatives is a dir
/etc/apache2 is a dir
/etc/apm is a dir
```

## Root the box

```bash
find . -exec /bin/sh \; -quit
```

Find SUID:
```bash
find / -perm /4000 2>/dev/null -exec ls -la {} \;
```

## String Manipulation

#### awk

```bash
# -F Delim = " "
# print 3rd 4th and 9th field and send to CSV
ls -l /etc | awk -F " " '{print$3","$4","$9}' > files.csv
```
