# Windows Auditing and Logging JSON

# 1. (10)
Prompt:
```
File: /home/garviel/conn.log

    Use jq to pretty print the JSON file conn.log.

    Hash the pretty-printed file with md5sum for the flag.
```

Steps:
```
garviel@terra:~$ jq . conn.log | md5sum
```

Answer:
```
25ebedf7442e470eaaa48b5f7d5b96f4
```

# 2. (10)
Prompt:
```
File : /home/garviel/conn.log

This file is a conn.log made in Zeek (Bro) with data about TCP/IP connections.

Use jq to locate and count the unique originating endpoint IP addresses in the file. Enter the number of unique originating IP addresses as the flag.

Flag format: #
```

Steps:
```
garviel@terra:~$ jq . conn.log | grep id.orig_h | sort | uniq | wc -l
31
```

Answer:
```
31
```

# 3. (10)
Prompt:
```
File: /home/garviel/conn.log

This file is a conn.log made in Zeek (Bro) with data about TCP/IP connections.

Use jq to locate and count connections where the destination IP sent more than 40 bytes to the source IP.

Flag format: #
```

Steps:
```
garviel@terra:~$ jq '. | select(.resp_bytes > 40) | [.orig_bytes]' conn.log | grep [0-9] | wc -l     
177
```

Answer:
```
177
```
