# Windows AD Basics

# 1. (5)
Prompt:
```
What PowerShell command will list domain groups?
```

Answer:
```
Get-ADGroup
```

# 2. (5)
Prompt:
```
What PowerShell command will list all users and their default properties?

The flag is the full command with arguments.
```

Answer:
```
Get-ADUser -Filter *
```

# 3. (10)
Prompt:
```
How many users are members of the Domain Admins group?

HINT: No sub-groups.
```

Steps:
```
PS C:\> Get-ADGroupMember -Identity "Domain Admins"
```

Answer:
```
1
```

# 4. (10)
Prompt:
```
How many total users are members of the Domain Admins group?
```

Steps:
```
Get-ADGroupMember -Identity "Domain Admins" -Recursive | measure
```

Answer:
```
14
```

# 5. (5)
Prompt:
```
What PowerShell command will allow you to search Active Directory accounts for expired accounts without having to create a filter?

The flag is only the command, no arguments/switches.
```

Answer:
```
Search-ADAccount
```

# 6. (10)
Prompt:
```
Find the short name of the domain in which this server is a part of.
```

Steps:
```
PS C:\> Get-ADDomainController -Filter *        

ComputerObjectDN           : CN=DOMAIN-CONTROLL,OU=Domain Controllers,DC=army,DC=warriors
DefaultPartition           : DC=army,DC=warriors     
Domain                     : army.warriors       
Enabled                    : True    
```

Answer:
```
army
```

# 7. (10)
Prompt:
```
What is the RID of the krbtgt account.
```

Steps:
```
PS C:\> Get-ADUser -Filter {Name -eq "krbtgt"}

DistinguishedName : CN=krbtgt,CN=Users,DC=army,DC=warriors
Enabled           : False
GivenName         :
Name              : krbtgt
ObjectClass       : user
ObjectGUID        : 5be4da40-22c3-4b7e-8d5f-1e0174413736
SamAccountName    : krbtgt
SID               : S-1-5-21-427089730-1199744433-1189759946-502
Surname           :
UserPrincipalName :  
```

Answer:
```
502
```

# 8. (5)
Prompt:
```
What is the domain portion of the following SID:

S-1-5-21-1004336348-1177238915-682003330-1000
```

Answer:
```
21-1004336348-1177238915-682003330
```
