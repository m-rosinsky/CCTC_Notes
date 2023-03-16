# Windows Powershell
This subfolder contains notes and writeups pertaining to the Windows Powershell module.

Start Flag: `start2347`

## 1. PRIMER_CLI_1

Prompt:
```
Which program starts with every CMD and PowerShell instance in Windows 7 and later?

Research: https://devblogs.microsoft.com/commandline/windows-command-line-inside-the-windows-console/
```

Answer:
```
conhost.exe
```

## 2. PRIMER_CLI_2

Prompt:
```
What Windows 10 feature supports installing Linux subsystem?

Research: https://learn.microsoft.com/en-us/windows/wsl/about
```

Answer:
```
wsl
```

## 3. PRIMER_CLI_3

Prompt:
```
Which Windows feature can be used to interact with any CLI on the Windows system concurrently using multiple tabs?

Research: https://learn.microsoft.com/en-us/windows/terminal/
```

Answer:
```
Windows Terminal
```

## 4. PRIMER_CLI_4

Prompt:
```
What was the default shell of Windows versions Windows 2000 through Windows 8.1?

Research: https://learn.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher
```

Answer:
```
cmd
```

## 5. PRIMER_CLI_5

Prompt:
```
What data type do all cmd.exe commands return?

Research: https://en.wikipedia.org/wiki/Comparison_of_command_shells (Hint: What data type is "text"?)
```

Answer:
```
string
```

## 6. PRIMER_CLI_6

Prompt:
```
What framework is PowerShell built on?

Research: https://en.wikipedia.org/wiki/.NET
```

Answer:
```
.NET
```

## 7. PRIMER_CLI_7

Prompt:
```
"What will all of the below give you?

(get-host).version

$host.version

$psversiontable.psversion"

Research: https://devblogs.microsoft.com/scripting/powertip-check-version-of-powershell/
```

Answer:
```
powershell version
```

## 8. PRIMER_CLI_8

Prompt:
```
After PowerShell Core is installed what CLI command launches it?

Research: https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.2
```

Answer:
```
pwsh.exe
```

## 9. PRIMER_CLI_9

Prompt:
```
"After PowerShell Core is installed you can still run the built in version of PowerShell side-by-side. What CLI command will launch the built in version?"

Research: Primer_CLI_9 https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/powershell
```

Answer:
```
powershell.exe
```

## 10. Windows_PowerShell_Basics1 (5)

Prompt:
```
What syntax do PowerShell cmdlets follow?
```

Answer:
```
verb-noun
```

## 11. Windows_PowerShell_Basics2 (5)

Prompt:
```
What PS command will list all PowerShell cmdlets?
```

Answer:
```
Get-Command
```

## 12. Windows_PowerShell_Basics3 (5)

Prompt:
```
What PowerShell command will list all verbs?
```

Answer:
```
Get-Verb
```

## 13. Windows_PowerShell_Basics4 (5)

Prompt:
```
BASH commands output strings. PowerShell commands output what data type?
```

Answer:
```
object
```

## 14. Windows_PowerShell_Basics5 (5)

Prompt:
```
All PowerShell objects are comprised of what two things?

Flag format: things,things
```

Answer:
```
properties,methods
```

## 15. Windows_PowerShell_Basics6 (5)

Prompt:
```
What command will list all things that make up a PowerShell object?
```

Answer:
```
Get-Member
```

## 16. Windows_PowerShell_Alias1 (5)

Prompt:
```
What PowerShell command will list PowerShell aliases?
```

Answer:
```
Get-Alias
```

## 17. Windows_PowerShell_Alias2 (5)

Prompt:
```
What PowerShell command lists all of the contents of a directory?
```

Answer:
```
Get-ChildItem
```

## 18. Windows_PowerShell_Help1 (5)

Prompt:
```
What is the basic cmdlet that displays help about Windows Powershell cmdlets and concepts?
```

Answer:
```
Get-Help
```

## 18. Windows_PowerShell_Help2 (5)

Prompt:
```
PowerShell "help files" don't show the entire help file with a basic command. What switch option shows the entire help file?
```

Answer:
```
-Full
```

## 19. Windows_PowerShell_Help3 (5)

Prompt:
```
What PowerShell command will update the PowerShell "help files" to the latest version?
```

Answer:
```
Update-Help
```

## 20. Windows_PowerShell_Help5 (5)

Prompt:
```
What help switch will show you the "help files" on Microsoft's website, in your default browser?
```

Answer:
```
-Online
```

## 21. Windows_PowerShell_Interaction1 (5)

Prompt:
```
What command will start the Chrome browser on your machine?
```

Answer:
```
Start-Process chrome
```

## 22. Windows_PowerShell_Interaction2 (5)

Prompt:
```
What command using a PS Method will stop chrome?

Flag is the full command
```

Answer:
```
(Get-Process chrome).kill()
```

## 23. Windows_PowerShell_Interaction3 (5)

Prompt:
```
What PowerShell command (without using a method) will stop the Chrome process?
```

Answer:
```
Stop-Process -Name chrome
```

## 24. Windows_PowerShell_CimClasses1 (5)

Prompt:
```
PowerShell doesn't have a native cmdlet that will give you processor information (such as get-processor or get-cpu). Knowing this information might be necessary. What command would give you information about the system's processor?

Flag is the full command
```

Answer:
```
Get-WmiObject Win32_Processor
```

## 25. Windows_PowerShell_Logic1 (5)

Prompt:
```
What PowerShell command will read a text file?
```

Answer:
```
Get-Content
```

## 26. Windows_PowerShell_Logic2 (5)

Prompt:
```
What PowerShell command will allow for counting lines in a file, averaging numbers, and summing numbers?
```

Answer:
```
Measure-Object
```

## 27. Windows_PowerShell_Regex1 (5)

Prompt:
```
What PowerShell command searches for text patterns in a string?
```

Answer:
```
Select-String
```

## 28. Windows_PowerShell_Basics9 (5)

Prompt:
```
Users' files are stored in their corresponding home directory. What is the literal path to all home directories on a Windows 10 system?
```

Answer:
```
C:\Users
```

## 29. Windows_PowerShell_Basics7 (10)

Prompt:
```
How many properties are available for the get-process cmdlet?

Note: Property values only
```

```powershell
Get-Process | Get-Member | Where-Object {$_.MemberType -eq "Property"} | Measure-Object
```

Answer:
```
52
```

## 30. Windows_PowerShell_Alias3 (10)

Prompt:
```
How many aliases does PowerShell have for listing the contents of a directory?
```

Answer:
```
3
```

## 31. Windows_PowerShell_Help4 (10)

Prompt:
```
When requesting the help file for the get-process cmdlet, what full command is the 9th example given?
```

Answer:
```
Get-Process powershell
```

## 32. Windows_PowerShell_CimClasses2 (10)

Prompt:
```
To complete this challenge, find the description of the Lego Land service.
```

```powershell
Get-WmiObject win32_service | Where-Object {$_.Name -eq "LegoLand"} | select -Property *
```

Answer:
```
i_love_legos
```

## 33. Windows_PowerShell_Logic3 (10)

Prompt:
```
In the CTF folder on the CTF User's Desktop, count the number of words in words2.txt.
```

```powershell
Get-Content .\CTF\words2.txt | Measure-Object -word
```

Answer:
```
5254
```

## 34. Windows_PowerShell_Logic4 (10)

Prompt:
```
Count the number of files in the Videos folder in the CTF user's home directory.
```

```powershell
Get-ChildItem .\Videos\ | Measure-Object
```

Answer:
```
925
```

## 35. Windows_PowerShell_Logic5 (10)

Prompt:
```
Find the only line that makes the two files in the CTF user's Downloads folder different.

Hint The flag is the string (not line number).
```

```powershell
diff (Get-Content .\new.txt) (Get-Content .\old.txt)
```

Answer:
```
popeye
```

## 36. Windows_PowerShell_Logic6 (10)

Prompt:
```
The password is the 21st line from the top, in ASCII alphabetically-sorted, descending order of the words.txt file.

Note: File location is CTF user’s Desktop in CTF folder.
```

```powershell
Get-Content .\words.txt | Sort-Object -Descending | Select-Object -First 21
```

Answer:
```
ZzZp
```

## 37. Windows_PowerShell_Logic7 (10)

Prompt:
```
Count the number of unique words in words.txt, found on the CTF user's desktop, in the CTF folder.
```

```powershell
Get-Content .\words.txt | Sort-Object -Unique | Measure-Object -word
```

Answer:
```
456976
```

## 38. Windows_PowerShell_Basics8 (10)

Prompt:
```
How many methods are available for the get-process cmdlet?

Machine: Admin_Station
```

```powershell
Get-Process | Get-Member | Where-Object {$_.MemberType -eq "Method"} | Measure-Object
```

Answer:
```
19
```

## 39. Windows_PowerShell_Logic9 (10)

Prompt:
```
Count the number of folders in the Music folder in the CTF user’s profile.
```

```powershell
Get-ChildItem -Directory | Measure-Object
```

Answer:
```
411
```

## 40. Windows_PowerShell_Regex2 (10)

Prompt:
```
Count the number of times, case-insensitive, gaab is listed in words.txt in the CTF folder on the CTF user's desktop.
```

```powershell
Get-Content .\words.txt | Select-String "gaab" | Measure-Object
```

Answer:
```
1
```

## 41. Windows_PowerShell_Regex3 (10)

Prompt:
```
Count the number of words, case-insensitive, with either a or z in a word, in the words.txt file on the CTF user's desktop.

Hint: There are multiple "words" on each line.
```

```powershell
Get-Content .\words.txt | Select-String "[aAzZ]" | Measure-Object
```

Answer:
```
160352
```

## 42. Windows_PowerShell_Regex4 (10)

Prompt:
```
Count the number of times az appears in the words.txt file on the CTF user's desktop.
```

```powershell
Get-Content .\words.txt | Select-String "az" | Measure-Object
```

Answer:
```
2754
```

## 43. Windows_PowerShell_Logic8 (15)

Prompt:
```
Use a PowerShell loop to unzip the Omega file 1,000 times and read what is inside.

Note: Make sure you back up the .zip file to a different directory before attempting this challenge.
```

```powershell
for ($i = 1000; $i -gt 0; $i--) {
$fname = 'Omega' + $i + '.zip'
Expand-Archive $fname
$dirname = 'Omega' + $i
mv $dirname/* .
rm -recurse $dirname
rm $fname
}
```

Answer:
```
kung-fu
```

## 44. Windows_PowerShell_Regex5 (15)

Prompt:
```
On the CTF user's desktop, count the number of words in words.txt that meet the following criteria:

    a appears at least twice consecutively
    and is followed immediately by any of the letters a through g

Example: aac...aaa...
```

```powershell
Get-Content .\words.txt | Select-String "aa[a-g]" | Measure-Object
```

Answer:
```
357
```
