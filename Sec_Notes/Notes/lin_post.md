# Linux Post Exploitation Notes

Find sudo permissions:
```
sudo -l
```

Find SUIDs / GUIDs:
```
find / -type f -perm /2000 -ls 2>/dev/null
find / -type f -perm /4000 -ls 2>/dev/null
```

GTFObins for sudo privileges:
```
gtfobins.github.io
```

Add current dir to path:
```
PATH=$(pwd):$PATH /bin/[exec]
```

John:
```
john --wordlist=[list] shadow
```

Instructor Notes:
```
sudo -l

find / -type f -perm /4000 -ls 2>/dev/null # Find SUID only files
find / -type f -perm /2000 -ls 2>/dev/null # Find SGID only files
find / -type f -perm /6000 -ls 2>/dev/null # Find SUID and/or SGID files


john --wordlist=passwordlist shadow1

https://gtfobins.github.io
http://www.nncron.ru/help/EN/working/cron-format
https://www.the-art-of-web.com/system/rsyslog-config/
```
