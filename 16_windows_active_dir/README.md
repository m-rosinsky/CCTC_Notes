# Windows Active Directory Enumeration

Start Key: `start5557`

# 1. What is Active Directory?

- Allows network admins to create and manage domains, users, and objects

## 1.1 Active Directory Structure

- Domains
    - AD objects (users or devices) that all use same database

- Trees
    - Several domains grouped together
    - Typically has primary DC

- Forests
    - Groups of trees connected via trust relationships

| ![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/014_windows_active_directory_enumeration/pages/ADimage1.png "AD Objects") |
|:--:|

# 2. Enumerate Users

- Look for suspicious accounts

# 2.1 Initial Recon

```powershell
# Get list of AD commands
Get-Command -Module activedirectory

# Get default domain password policy
Get-ADDefaultDomainPasswordPolicy

# Check for any fine-grained password policies
Get-ADFineGrainedPasswordPolicy -Filter {name -like "*"}

# Get Forest Details
Get-ADForest

# Get Domain Details
Get-ADDomain
```

Groups:
```powershell
# Get AD Groups
Get-ADGroup -Filter *

# Get a groups details
Get-ADGroup -Identity 'Group Name'

# Get a list of group members
Get-ADGroupMember -Identity 'Group Name' -Recursive
```

Users:
```
# Get AD Users
Get-ADUser -Filter 'Name -like "*"'

# See additional user properties
Get-ADUser -Identity 'User Name' -Properties Description
```

## 2.2 Enumerate Users
```powershell
# Find Disabled Users
Get-ADUser -Filter {Enabled -eq "False"} -Properties name, enabled

# Enable said user
Enable-ADAccount -Identity guest

# Change the password
Set-AdAccountPassword -Identity guest -NewPassword (ConvertTo-SecureString -AsPlaintext -String "PassWord12345!!" -Force)

# Add user to admin group
Add-ADGroupMember -Identity "Domain Admins" -Members guest
```
