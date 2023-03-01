# Linux Basics

# 1. (5)
Prompt:
```
What command lists the contents of directories in Linux/Unix systems?
```

Answer:
```
ls
```

# 2. (5)
Prompt:
```
For the ls command, what arguments, or switch options, will allow you to print human-readable file sizes in a long-list format?

The flag is entire command, including arguments
```

Answer:
```
ls -lh
```

# 3. (5)
Prompt:
```
What character will pipe the standard output from

echo "I’m a plumber"

to another command, as standard input?
```

Answer:
```
|
```

# 4. (5)
Prompt:
```
What argument/switch option, when used with man, will search the short descriptions and man-page-names for a keyword that you provide?

The flag is the complete command, with argument/switch.
```

Answer:
```
man -k
```

# 5. (10)
Prompt:
```
Search the man pages for the keyword digest. Then, use one of the binaries listed to hash the string OneWayBestWay using the largest sha hash available.

The resulting hash is the flag.
```

Steps:
```
echo OneWayBestWay > hash.txt
sha512sum hash.txt
```

Answer:
```
a81bc463469ee1717fc9e388e3799c653f63a3de5e9496b5707b56488b046cbf75665235d316c5c0053a597dc7d40c917a2d9006fe35e9cb47766c05ac71989b
```

# 6. (10)
```
Use File: /home/garviel/Encrypted

This file contains encrypted contents. Identify its file type, then decode its contents.

Hint: Use OpenSSL
```

Steps:
```bash
unzip Encrypted

garviel@terra:~$ openssl enc -d -aes-128-cbc -in cipher -out file.txt
enter aes-128-cbc decryption password:
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.      
garviel@terra:~$ cat file.txt
DeCrypt
```

Answer:
```
DeCrypt
```
