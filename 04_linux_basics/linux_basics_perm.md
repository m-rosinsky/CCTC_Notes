# Linux Basics Permissions

# 1. (10)
Prompt:
```
Find the directory named Bibliotheca. Enter the absolute path to the directory.
```

Steps:
```bash
garviel@terra:~$ find / -name "Bibliotheca" 2>/dev/null
/media/Bibliotheca
```

Answer:
```
/media/Bibliotheca
```

# 2. (10)
Prompt:
```
Identify the number of users with valid login shells, who can list the contents of the Bibliotheca directory.
```

Steps:
```bash
garviel@terra:~$ cat /etc/group | grep "mephi"
mephiston:x:1008:
chapter:x:1009:garviel,tarik,aximand,ezekyle,sejanus,erebus,mephiston
```

Answer:
```
7
```

# 3. (10)
Prompt:
```
The permissions that user sejanus has on /media/Bibliotheca, in octal format.

Flag format: #

HINT: Think about groups...
```

Steps:
```bash
# User has r-x perms since he is in group. 4(r) + 1(x) = 5.
```

Answer:
```
5
```

# 5. (10)
Prompt:
```
Locate the file within /media/Bibliotheca that is modifiable by the only user that is part of the Chapter group, but not part of the Lodge group.

Hint: Not the hidden file...
```

Steps:
```bash
cat /etc/group | grep "lodge"
cat /etc/group | grep "chapter"

# User in chapter, but not lodge -> mephiston

ls -l /media/Bibliotheca/*
-rw-r----- 1 mephiston chapter 4121 Feb 28  2022  Codex_Astartes
```

Answer:
```
Codex_Astartes
```

# 7. (10)
Prompt:
```
Identify the file within /media/Bibliotheca where the owning group has more rights than the owning user.
```

Steps:
```bash
ls -l /media/Bibliotheca/*
-r--rw-r-- 1 mephiston guardsmen 4047 Feb 28  2022  Codex_Imperium
```

Answer:
```
Codex_Imperium
```

# 8. (10)
Prompt:
```
Execute the file owned by the guardsmen group in /media/Bibliotheca, as the owning user.

The flag is the code name provided after a successful access attempt.
```

Steps:
```bash
ls -l /media/Bibliotheca/*
-rwxrwx--- 1 gaunt     guardsmen  865 Feb 28  2022  Tactica_Imperium
```

Answer:
```

```
