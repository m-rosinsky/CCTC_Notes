# Windows AD Search

# Accounts (10)
Prompt:
```
Find the expired accounts that aren't disabled. List the last names in Alphabetical Order, separated with a comma, and no space between.

Flag format: name,name
```

Steps:
```
PS C:\Users\andy.dwyer> Search-ADAccount -AccountExpired
```

Answer:
```
Krause,Page
```

# Emails (10)
Prompt:
```
Find the unprofessional email addresses. List the email's domain.
```

Steps:
```
PS C:\Users\andy.dwyer> Get-ADUser -Properties EmailAddress -Filter * | select name,EmailAddress | Se
lect-String -notmatch "mail.mil"
```

Answer:
```
ashleymadison.com
```

# Files (10)
Prompt:
```
The flag is the unprofessionally-named file located somewhere on the Warrior Share.

Connect to the Warrior Share:

net use * "\\file-server\warrior share"
```

Steps:
```
PS C:\Users\andy.dwyer> net use * "\\file-server\warrior share"
Drive Z: is now connected to \\file-server\warrior share.

The command completed successfully.

PS C:\Users\andy.dwyer> cd 'Z:'                
PS Z:\> gci -Recurse
```

Answer:
```
lulz.pdf
```

# Insider 1 (10)
Prompt:
```
The flag is the name of the user who is requesting modified access rights.
```

Steps:
```
Gci for files. 14827.pdf
```

Answer:
```
14287.pdf
```

# Insider 2 (10)
Prompt:
```
The flag is the name of the user who is requesting modified access rights.
```

Steps:
```

```

Answer:
```
Karen.Nance
```

# Naming (10)
Prompt:
```
Find the accounts that contain unprofessional information in the description.

List the last names in Alphabetical Order, separated by a comma, with no space.

Flag format: name,name
```

Steps:
```
Get-ADUser -Filter * -Properties description | select name,description

Xavier.Ibarra       description

Raegan.Lee          description
```

Answer:
```
Ibarra,Lee
```

# Passwords (10)
Prompt:
```
Find the following three accounts:

    two accounts with passwords that never expire
    one account that has its password stored using reversible encryption

List the last names in Alphabetical Order, comma-separated, no spaces. Do not list built-in accounts.

Flag format: name,name,name
```

Steps:
```
PS C:\> Get-ADUser -Filter {AllowReversiblePasswordEncryption -eq "True"}

DistinguishedName : CN=Alice.Brandywine,OU=S-6,OU=STAFF,OU=HQ,OU=WARRIORS,DC=army,DC=warriors        
Enabled           : True
GivenName         : Alice
Name              : Alice.Brandywine

PS C:\> Get-ADUser -Filter {PasswordNeverExpires -eq "True"} -Properties PasswordNeverExpires | selec
t Name,PasswordNeverExpires

Name           PasswordNeverExpires
----           --------------------
Eddie.Sanchez                  True
Xavier.Ibarra                  True

```

Answer:
```
brandywine,ibarra,sanchez
```

# PII (10)
Prompt:
```
The flag is the name of the file containing PII on the Warrior Share.
```

Steps:
```
gci-recurse
```

Answer:
```
phone_matrix.xlsx
```
