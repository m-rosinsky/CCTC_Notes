# Windows Prefetch

# 1. (5)
Prompt:
```
What is the literal path of the prefetch directory?
```

Answer:
```
C:\Windows\Prefetch
```

# 2. (5)
Prompt:
```
Enter the name of the questionable file in the prefetch folder.
```

Answer:
```
DARK_FORCES-8F2869FC.pf
```

# 3. (5)
Prompt:
```
What is the creation time of the questionable file in the prefetch folder?

Flag format: mm/dd/yyyy
```

Steps:
```
PS HKLM:\SYSTEM\CurrentControlSet\Services\bam\UserSettings\> ls C:\Windows\Prefetch\DARK_FORCES-8F28
69FC.pf | select *
```

Answer:
```
02/23/2022
```
