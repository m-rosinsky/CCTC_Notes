# Linux Boot MBR

# 1. (5)
Prompt:
```
How large is the Master Boot Record and what directory is it located in?

Flag format: #InBytes,directory
```

Answer:
```
512,/dev
```

# 2. (10)
Prompt:
```
Locate the master boot record for one of the Linux machines and read it with xxd

What programming language is the MBR written in?

HINT: Look at the first three bytes
```

Answer:
```
assembly
```

# 3. (10)
Prompt:
```
The file /home/bombadil/mbroken is a copy of an MBR from another machine.

Hash only the Bootstrap section of the MBR using md5sum. The flag is the entire hash.
```

Steps:
```bash
bombadil@minas-tirith:~$ dd if=mbroken of=part2.txt bs=446 count=1 skip=0 iflag=skip_bytes
1+0 records in
1+0 records out
446 bytes copied, 0.000307043 s, 1.5 MB/s
bombadil@minas-tirith:~$ md5sum part2.txt
d59a68c7b6d62ecaa1376dfb73a3b7be  part2.txt
bombadil@minas-tirith:~$
```

Answer:
```
d59a68c7b6d62ecaa1376dfb73a3b7be
```

# 4. (10)
Prompt:
```
The file /home/bombadil/mbroken is a copy of an MBR from another machine.

Hash the first partition of the file using md5sum. The flag is the hash.
```

Steps:
```bash
bombadil@minas-tirith:~$ dd if=mbroken of=part1.txt bs=16 count=1 skip=446 iflag=skip_bytes              
1+0 records in
1+0 records out
16 bytes copied, 0.000137571 s, 116 kB/s
bombadil@minas-tirith:~$ ls -l
total 8
-rw-r--r-- 1 bombadil bombadil 512 Oct 13  2021 mbroken  
-rw-r--r-- 1 bombadil bombadil  16 Mar  3 17:56 part1.txt
bombadil@minas-tirith:~$ md5sum part1.txt
2a5948fad4ec68170b23faaa2a16cef8  part1.txt
```

Answer:
```
2a5948fad4ec68170b23faaa2a16cef8
```

# 5. (10)
Prompt:
```
The file /home/bombadil/mbroken is a copy of an MBR from another machine.

You will find the "word" GRUB in the output, hash using md5sum.

The flag is the entire hash.
```

Steps:
```bash
bombadil@minas-tirith:~$ dd if=mbroken of=part2.txt bs=4 count=1 skip=392 iflag=skip_bytes
1+0 records in
1+0 records out
4 bytes copied, 0.000761875 s, 5.3 kB/s
bombadil@minas-tirith:~$ md5sum part2.txt
5fa690cb0f0789cbc57decfd096a503e  part2.txt
bombadil@minas-tirith:~$
```

Answer:
```
5fa690cb0f0789cbc57decfd096a503e
```
