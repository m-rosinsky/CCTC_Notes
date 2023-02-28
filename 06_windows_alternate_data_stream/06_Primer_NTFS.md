## 1. Primer_NTFS_1 (1)
Prompt:
```
The ____ determines how the data is stored on disk.

(Fill in the blank)

Research: https://social.technet.microsoft.com/wiki/contents/articles/5375.windows-file-systems.aspx
```

Answer:
```
File System
```

## 2. Primer_NTFS_2 (1)
Prompt:
```
What are NTFS partition sectors grouped into?

Research: https://learn.microsoft.com/en-us/windows-server/storage/file-server/ntfs-overview
```

Answer:
```
Clusters
```

## 3. Primer_NTFS_3 (1)
Prompt:
```
What contains the metadata about all of the files and directories on a NTFS partition?

Research: https://learn.microsoft.com/en-us/windows/win32/devnotes/master-file-table
```

Answer:
```
Master File Table
```

## 4. Primer_NTFS_4 (1)
Prompt:
```
NTFS files are collections of what?

(Hint: What are the user data streams? or all streams for that matter) Research: https://learn.microsoft.com/en-us/windows/win32/devnotes/master-file-table
```

Answer:
```
Attributes
```

## 5. Primer_NTFS_5 (1)
Prompt:
```
Which NTFS attribute would store an alternate data stream?

Research: https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-fscc/c54dec26-1551-4d3a-a0ea-4fa40f848eb3
```

Answer:
```
$DATA
```

## 6. Primer_NTFS_6 (1)
Prompt:
```
Which NTFS attribute holds information about a file's encrypted attributes?

Research:

https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-fscc/a82e9105-2405-4e37-b2c3-28c773902d85
```

Answer:
```
$LOGGED_UTILITY_STREAM
```

## 7. Primer_NTFS_7 (1)
Prompt:
```
Which NTFS attribute that is composed of the file security and access control properties?

Research: https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-fscc/a82e9105-2405-4e37-b2c3-28c773902d85
```

Answer:
```
$SECURITY_DESCRIPTOR
```

## 8. Primer_NTFS_8 (1)
Prompt:
```
In NTFS, what is the type id, in hex, of the attribute that actually stores a NTFS files contents?

Research: https://flatcap.github.io/linux-ntfs/ntfs/attributes/data.html
```

Answer:
```
0x80
```

## 9. Primer_NTFS_9 (1)
Prompt:
```
In NTFS what is the maximum number of bytes a MFT entry (containing the entirety of a file) can contain to be considered "Resident Data"?

Research: https://www.sciencedirect.com/topics/computer-science/master-file-table https://en.wikipedia.org/wiki/NTFS
```

Answer:
```
1024
```

## 10. Primer_NTFS_10 (1)
Prompt:
```
NTFS permissions can be a assigned to a filesystem object in two ways. Which way is intentionally assigned on the file or folder?

Research: https://devblogs.microsoft.com/scripting/weekend-scripter-use-powershell-to-get-add-and-remove-ntfs-permissions/
```

Answer:
```
Explicit
```

## 11. Primer_NTFS_11 (1)
Prompt:
```
NTFS permissions can be a assigned to a filesystem object in two ways. Which way is the results of an object being assigned permissions as the result of being the child of another object?

Research: https://devblogs.microsoft.com/scripting/weekend-scripter-manage-ntfs-inheritance-and-use-privileges/
```

Answer:
```
inherited
```

## 12. Primer_NTFS_12 (1)
Prompt:
```
Which NTFS file level permission is missing from the following list? Write, Read & Execute, Modify, Full Control

Research: https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc783530(v=ws.10)?redirectedfrom=MSDN
```

Answer:
```
read
```

## 13. Primer_NTFS_13 (1)
Prompt:
```
Which NTFS folder level permission is missing from the following list?: Read, Write, Read & Execute, Modify, Full control

Research: https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc783530(v=ws.10)?redirectedfrom=MSDN
```

Answer:
```
list folder contents
```

## 14. Primer_NTFS_14 (1)
Prompt:
```
Which NTFS file level permission permits changing the contents of a file, deleting the file but does not allow the ability to change the permissions on the file?

Research: https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc783530(v=ws.10)?redirectedfrom=MSDN
```

Answer:
```
Modify
```

## 15. Primer_NTFS_15 (1)
Prompt:
```
Which NTFS folder level permission allows changing permissions?

Research: https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc783530(v=ws.10)?redirectedfrom=MSDN
```

Answer:
```
Full control
```

## 16. Primer_NTFS_16 (1)
Prompt:
```
Which NTFS attribute stores the file times of an object?

Research: https://flatcap.github.io/linux-ntfs/ntfs/attributes/standard_information.html
```

Answer:
```
$STANDARD_INFORMATION
```

## 17. Primer_NTFS_17 (1)
Prompt:
```
What CLI command will only show the letters of attached drives? **Hint command is 3 words

Research: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-fsinfo
```

Answer:
```
fsutil fsinfo drives
```
