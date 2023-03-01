# Linux Basics Regex

# 1. (10)
Prompt:
```
Using the commands ls and grep, identify the number of directories in /etc/ that end in .d
```

Steps:
```bash
garviel@terra:/media/Bibliotheca$ ls -A /etc/ | grep "\.d$" | wc -l
28
```

Answer:
```
28
```

# 2. (10)
Prompt:
```
File: home/garviel/numbers

Use regular expressions to match patterns similar to an IP address.

The answer is the count/number of lines that match in the file.
```

Steps:
```bash
garviel@terra:~$ grep -E '^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}$' numbers | wc -l
78
```

Answer:
```
78
```

# 3. (10)
Prompt:
```
File: home/garviel/numbers

Use regular expressions to match valid IP addresses. The flag is the number of addresses.

HINT: What are the valid numerical values of each octet in an IP address?
```

Steps:
```bash
garviel@terra:~$ grep -E '^((25[0-5]|2[0-4][0-9]|[1]?[1-9][0-9]?).){3}(25[0-5]|2[0-4][0-9]|[1]?[1-9]?
[0-9])$' numbers | wc -l
18
```

Answer:
```
18
```

# 4. (10)
Prompt:
```
File: home/garviel/numbers

Use regular expressions to match patterns that look similar to a MAC Address. Flag is a count of the number of matches.

HINT: This is a loose match! Some of these results won't be true MAC addresses.

Flag format: ####
```

Steps:
```bash
garviel@terra:~$ grep -E '^(([A-Z]|[0-9]){2}-){5}([A-Z]|[0-9]){2}$' numbers | wc -l
4877
```

Answer:
```
4877
```

# 5. (15)
Prompt:
```
File: home/garviel/numbers

Use regular expressions to find valid Locally Administered or Universally Administered Unicast MAC addresses.

Give the count of Locally and Universally Administered MAC addresses as the answer.

HINT: What characters specifically define a Locally or Universally Administered Unicast MAC Address?
```

Steps:
```bash
# There are 4 ranges of Locally Administered Address Ranges that can be used on a local network:

    # x2-xx-xx-xx-xx-xx
    # x6-xx-xx-xx-xx-xx
    # xA-xx-xx-xx-xx-xx
    # xE-xx-xx-xx-xx-xx

    # x0
    # x4
    # x8
    # xC

garviel@terra:~$ grep -E '^(([A-F]|[0-9])(0|2|4|6|8|A|C|E))-((([A-F]|[0-9]){2})-){4}(([A-F]|[0-9]){2})$' numbers | wc -l
178

```

Answer:
```
178
```
