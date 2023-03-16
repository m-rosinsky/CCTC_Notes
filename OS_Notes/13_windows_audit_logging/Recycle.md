# Windows Recycle Bin

# 1. (5)
Prompt:
```
In the Recycle Bin, there is a file that contains the actual contents of the recycled file. What are the first two characters of this filename?
```

Answer:
```
$R
```

# 2. (5)
Prompt:
```
In the Recycle Bin, there is a file that contains the original filename, path, file size, and when the file was deleted. What are the first two characters of this filename?
```

Answer:
```
$I
```

# 3. (5)
Prompt:
```
Recover the flag from the Recycle Bin. Enter the name of the recycle bin file that contained the contents of the flag, and the contents of the deleted file.

Flag format: filename,contents
```

Steps:
```
PS C:\> $RBINCONT=$(ls 'C:\$RECYCLE.BIN' -Recurse -Verbose -Force | select FullName)
PS C:\> echo $RBINCONT | Out-File file.txt

PS C:\> foreach($line in Get-Content .\file.txt) {
>> echo $line; Get-Content $line }
```

Answer:
```
$RV3TKCJ.txt,DontTrashMeyo
```
