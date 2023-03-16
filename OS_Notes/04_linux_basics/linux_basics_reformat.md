# Linux Basics Reformat

# 1. (10)

Prompt:
```
File: home/garviel/numbers

Use awk to print lines:

>= 420 AND <=1337

The flag is a SHA512 hash of the output.
```

Steps:
```bash
garviel@terra:~$ awk 'NR==420, NR==1337' numbers | sha512sum
e62ff70d772ef0977f4f8fe1751fda5689ce1daf1fabc6d0cc49da234d02719986c0acb97f582166170a5a1f418e854602a5eb98c773655906a3f85440c37d39
```

Answer:
```
e62ff70d772ef0977f4f8fe1751fda5689ce1daf1fabc6d0cc49da234d02719986c0acb97f582166170a5a1f418e854602a5eb98c773655906a3f85440c37d39
```

# 2. (10)

Prompt:
```
File: home/garviel/connections

Use awk to create a separate CSV (comma separated value) file that contains columns 1-6.

The flag is an MD5 hash of the new file

Hint: Look at #fields on line 6 in the file to understand column layout.

Hint: This is a Zeek (formally known as Bro) connection log file in TSV format. Click This Link to learn about its formatting.
```

Steps:
```bash
garviel@terra:~$ cat connections | awk -F '\x09' '{print$1","$2","$3","$4","$5","$6}' > table.csv    
garviel@terra:~$ md5sum table.csv
6cebf155e9c8f49d76ae1268214ff0b5  table.csv
```

Answer:
```
6cebf155e9c8f49d76ae1268214ff0b5
```

# 4. (10)

Prompt:
```
This challenge is worth 0 POINTS, and should only be attempted after all other challenges that are open to you, are completed!

File: /home/garviel/NMAP_all_hosts.txt

Format the file into the output displayed below using native Linux binaries like awk.


Service: ident Count: 1
==============================
192.168.33.236

Service: IIS Count: 3
==============================
192.168.33.205
192.168.33.227
192.168.33.229

--TRIMMED--

Present the script used to the instructor for credit when complete. Be prepared to explain the code.

HINT: awk is a powerful text manipulation scripting language. It is a bit challenging to learn. Use the tutorials below to get started.

https://www.grymoire.com/Unix/Awk.html

https://www.gnu.org/software/gawk/manual/gawk.html
```

Steps:
```bash

```

Answer:
```

```
