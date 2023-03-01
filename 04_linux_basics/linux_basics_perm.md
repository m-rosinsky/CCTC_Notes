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

# 4. (10)
Prompt:
```
The user tyborc is unable to access the directory:

/media/Bibliotheca/Bibliotheca_unus

Why? Identify the permission missing in standard verb form.
```

Steps:
```bash
garviel@terra:~$ ls -l /media/Bibliotheca
total 16
drwxr-xr-x 7 mephiston chapter 4096 Feb 28  2022 Bibliotheca_duo     
dr-xr-xr-x 2 mephiston chapter 4096 Feb 28  2022 Bibliotheca_quattuor
dr-xr-xr-x 2 mephiston chapter 4096 Feb 28  2022 Bibliotheca_tribus  
dr-xr-xr-- 2 mephiston chapter 4096 Feb 28  2022 Bibliotheca_unus
```

Answer:
```
execute
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

# 6. (10)
Prompt:
```
You only have a single submission attempt for this challenge.

Locate the file in /media/Bibliotheca that Inquisitor Quixos has sole modification rights on.

The flag is the absolute path for the file.
```

Steps:
```bash

```

Answer:
```
/media/Bibliotheca/Bibliotheca_duo/Codex_Hereticus
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
sudo -H -u gaunt /media/Bibliotheca/Bibliotheca_quattuor/Tactica_Imperium

Tactica_Imperium

Enter_Access_Code
Only the owner may access this file:
Speak thy name: gaunt
Processing...Access Granted
Codename: GHOSTS
```

Answer:
```
GHOSTS
```

# 9. (10)
Prompt:
```
Read the concealed file within /media/Bibliotheca
```

Steps:
```bash
garviel@terra:/media/Bibliotheca$ ls -RA | grep "^\." | grep -v "warp"
.:
./Bibliotheca_duo:
.Secrets_of_the_Immaterium
.secrets
./Bibliotheca_quattuor:
.Secrets_of_the_Immeterium
./Bibliotheca_tribus:
./Bibliotheca_unus:
garviel@terra:/media/Bibliotheca$ cat Bibliotheca_duo/.Secrets_of_the_Immaterium
Expand your mind
```

Answer:
```
Expand your mind
```

# 10. (10)
Prompt:
```
Find the warp and read its secrets for the flag.
```

Steps:
```bash
garviel@terra:/media/Bibliotheca$ ls -RAp | grep -v /

garviel@terra:/media/Bibliotheca$ find . -name .secrets
./Bibliotheca_duo/.warp2/.warp5/warp5/.warp3/warp2/.secrets
garviel@terra:/media/Bibliotheca$ cat ./Bibliotheca_duo/.warp2/.warp5/warp5/.warp3/warp2/.secrets
Ph'nglui mglw'nafh Cthulhu
garviel@terra:/media/Bibliotheca$
```

Answer:
```
Ph'nglui mglw'nafh Cthulhu
```
