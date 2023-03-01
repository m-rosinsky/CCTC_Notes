# Linux Basics LFS Hierarchy

# 1. (5)
Prompt:
```
What is the absolute path to the root directory?
```

Answer:
```
/
```

# 2. (5)
Prompt:
```
What is the absolute path to the default location for configuration files?
```

Answer:
```
/etc
```

# 3. (5)
Prompt:
```
What is the directory that contains executable programs (binaries) which are needed in single user mode, to bring the system up or to repair it?
```

Answer:
```
/bin
```

# 4. (5)
Prompt:
```
What is the absolute path to the directory which contains non-essential binaries that are accessible by standard users as well as root?
```

Answer:
```
/usr/bin
```

# 5. (5)
Prompt:
```
An absolute path to a directory which contains binaries only accessible by the root user, or users in the root group.
```

Answer:
```
/sbin
```

# 5. (5)
Prompt:
```
An absolute path to a directory which contains binaries only accessible by the root user, or users in the root group.
```

Answer:
```
/usr/share/man/man1/cat.1.gz
```

# 7. (10)
Prompt:
```
Search the user home directories to find the file with the second-most lines in it. Hint: Exclude the VDI file! The flag is the number of lines in the file.
```

Steps:
```bash
garviel@terra:~$ files=$(find . ! -name '*vdi*')

garviel@terra:~$ for file in $files; do wc -l $file; done
wc: .: Is a directory
0 .
9 ./Encrypted
1 ./symmetric
20000 ./numbers
9 ./.bash_logout
3 ./.lesshst
40 ./Inquisition_Targets
172 ./.bash_history
2825 ./output.xml
29 ./.profile
0 ./cipher
6525 ./connections
wc: ./.gnupg: Is a directory
0 ./.gnupg
wc: ./.gnupg/private-keys-v1.d: Is a directory
0 ./.gnupg/private-keys-v1.d
867 ./NMAP_all_hosts.txt
183 ./files.csv
1 ./file.txt
990 ./paths
83892 ./conn.log
wc: ./Battlefield: Is a directory
0 ./Battlefield
30 ./Battlefield/titan_commands
24 ./Battlefield/minefield_map
117 ./.bashrc
wc: ./.cache: Is a directory
0 ./.cache
0 ./.cache/motd.legal-displayed
```

Answer:
```
20000
```
