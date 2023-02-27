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

```
