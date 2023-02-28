# Windows Registry Notes

The windows registry stores all information about the operating system.

## Registry Hives

- `HKEY_CLASSES_ROOT`
- `HKEY_CURRENT_USER`
- `HKEY_LOCAL_MACHINE`
- `HKEY_USERS`
- `HKEY_CURRENT_CONFIG`

## HKEY_USERS

#### SID

A SID (Security Identifier) are unique to each user on the system.

One key per user.

```powershell
# List the usernames and associated SIDs
Get-LocalUser | select name,sid
```

The registry entry under that SID within the `HKEY_USERS` hive mirrors the
`HKEY_CURRENT_USER` hive.

## HKEY_LOCAL_MACHINE

#### Run

```
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```

The run key will automatically run anything in this key on startup.

There are user run keys and machine run keys.

#### Run Once

```
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce
```

Same thing as `Run` but only for once.

## Entries

Entries have Name, Type, and Data

#### Data Types

- `REG_BINARY`
- `REG_DWORD`
- `REG_QWORD`
- Many more

## Registry Manipulation with PowerShell

#### Queries

```powershell
# Get the items in one or more specified locations.
Get-ChildItem [keypath]

# Get the properties of a key or subkey.
Get-ItemProperty

# Get item at location. Doesn't get contents unless * is used.
Get-Item
```

```powershell
# Get subkeys of Run
Get-ChildItem HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run

# Get values in Run
Get-Item HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```

#### Modifiers

```powershell
# Change value of a property.
Set-ItemProperty

# Remove a reg value.
Remove-ItemProperty
```

#### Create

```powershell
# Specify a reg path to create a new key.
New-Item

# Create new reg value.
New-ItemProperty
```

## Command Line RegEdit

```cmd
reg /?

reg query HKLM\Software\Microsoft\Windows\CurrentVersion\Run

reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run /v testme /t REG_SZ /d
 C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe

reg delete HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run /v testme
```
