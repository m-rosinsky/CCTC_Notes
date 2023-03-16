# Windows Jump Lists

# 1. (10)
Prompt:
```
gci -Recurse C:\users\*\AppData\Roaming\Microsoft\Windows\Recent\ | % {C:\sysinternalssuite\strings.exe -accepteula $_} >> c:\recentdocs.txt

cat recentdocs.txt | findstr \
```

Answer:
```
UIDPWD.txt
```
