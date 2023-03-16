# Linux Basics Users and Groups

# 1. (10)
Prompt:
```
Read the file that contains the user database for the machine. Identify a strange comment.
```

Steps:
```bash
garviel@terra:~$ more /etc/passwd | grep -v 'nologin'
root:x:0:0:root:/root:/bin/bash
sync:x:4:65534:sync:/bin:/bin/sync
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
lxd:x:105:65534::/var/lib/lxd/:/bin/false
pollinate:x:110:1::/var/cache/pollinate:/bin/false
ubuntu:x:1000:1000:Ubuntu:/home/ubuntu:/bin/bash
garviel:x:1001:1001:Traitor:/home/garviel:/bin/bash
tarik:x:1002:1002::/home/tarik:/bin/bash
aximand:x:1003:1003::/home/aximand:/bin/bash
ezekyle:x:1004:1004::/home/ezekyle:/bin/bash
sejanus:x:1005:1005::/home/sejanus:/bin/bash
erebus:x:1006:1006::/home/erebus:/bin/bash
mephiston:x:1007:1008::/home/mephiston:/bin/bash
gaunt:x:1008:1011::/home/gaunt:/bin/bash
amim:x:1009:1012::/home/amim:/bin/bash
tyborc:x:1010:1013::/home/tyborc:/bin/bash
karis:x:1011:1014::/home/karis:/bin/bash
quixos:x:1132:1136::/home/quixos:/bin/bash
```

Answer:
```
Traitor
```

# 2. (10)
Prompt:
```
Identify all members of the lodge group. List their names in alphabetical order with a comma in between each name.

Flag Format: name,name,name
```

Steps:
```bash
garviel@terra:~$ cat /etc/group | grep lodge | sed -e $'s/,/\\\n/g' | sort | grep -v "lodge" | tr '\n
' ','
aximand,erebus,ezekyle,garviel,sejanus,tarik
```

Answer:
```
aximand,erebus,ezekyle,garviel,sejanus,tarik
```

# 3. (10)
Prompt:
```
Find the user with a unique login shell.
```

Steps:
```bash
garviel@terra:~$ cat /etc/shells
# /etc/shells: valid login shells
/bin/sh
/bin/bash
/bin/rbash
/bin/dash
/usr/bin/tmux
/usr/bin/screen

garviel@terra:~$ cat /etc/passwd | grep /bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
```

Answer:
```
nobody
```

# 4. (10)
Prompt:
```
Identify the algorithm, the amount of salted characters added, and the length of the hashed password in the file that stores passwords.

Hint: Research 'padding'...

Flag format: algorithm,#characters,#length
```

Steps:
```bash
garviel:$6$4EghS31f$iauyWex09Mc9yaKYUR31z1AigzVIRBPxUr4J9NSgfpxHTOwwhsOM1gxZkPrwW1H2W9wEi4npIHZzzFKIj
u6TI0:19051:0:99999:7:::

# $6$ - sha512
# Salt - 4EghS31f - 7
# Password - iauyWex09Mc9yaKYUR31z1AigzVIRBPxUr4J9NSgfpxHTOwwhsOM1gxZkPrwW1H2W9wEi4npIHZzzFKIj
# Password len - 86
u6TI0
```

Answer:
```
sha512,8,86
```
