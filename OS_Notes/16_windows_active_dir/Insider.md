# Windows AD Follow Insider Trail

# 1. (15)
Prompt:
```
Continue to follow the insider trail to find additional insider threats and their compromised mission.

The flag is the full name of the next insider threat identified.

HINT: Search the Active Directory record of the user identified in search_insider_2.
```

Steps:
```
PS C:\> Get-ADUser -Filter {Name -eq "Karen.Nance"} -Properties *

StreetAddress                        : rkcrpg zl arkg pbzzhavpngvba ng 06:30 uef gbzbeebj zbeavat.   
                                       Ybpngvba sbe qrgnvyf vaibyivat n uvtuyl pynffvsvrq bcrengvba  
                                       hcybnqrq gb Gvssnal .

ROT-13:
expect my next communication at 06:30 hrs tomorrow morning.
Location for details involving a highly classified operation
uploaded to Tiffany . .

PS C:\> Get-ADUser -Filter {Name -like "*Tiffany*"} -Properties *
```

Answer:
```
Tiffany.Bellacino
```

# 2. (15)
Prompt:
```
Continue to follow the insider trail to find additional insider threats and their compromised mission.

The flag is the username resulting from assembling clues within a user's records.

HINT: Search the Active Directory record of the user identified in follow_insider_trail_1. Piece together clues to identify another insider threat.
```

Steps:
```
PS C:\> Get-ADUser -Filter {Name -like "*Tiffany*"} -Properties *

City                                 : mi
l                                    : mi
Office                               :  le
physicalDeliveryOfficeName           :  le
PostalCode                           : da
st                                   : an
State                                : an
StreetAddress                        : wis

PS C:\> Get-ADUser -Filter {Name -like "*lewis*"}
DistinguishedName : CN=Damian.Lewis,OU=1ST PLT,OU=ACO,OU=2NDBN,OU=WARRIORS,DC=army,DC=warriors       
Enabled           : True
GivenName         : Damian
Name              : Damian.Lewis
```

Answer:
```
damian.lewis
```

# 3. (15)
Prompt:
```
Continue to follow the insider trail to find additional insider threats and their compromised mission.

The flag is the full name of the insider threat identified.

HINT: Search the Active Directory record for the user identified in follow_insider_trail_2.
```

Steps:
```
PS C:\> Get-ADUser -Filter {Name -eq "damian.lewis"} -Properties *

info                                 : P0P SECRET - Star Wars Rogue One, opening night tomorrow!     
                                       Get em before they sell out! -Isiah

PS C:\> Get-ADUser -Filter {Name -like "*isiah*"}

DistinguishedName : CN=Isiah.Jesus,OU=1ST PLT,OU=CCO,OU=2NDBN,OU=WARRIORS,DC=army,DC=warriors        
Enabled           : True
GivenName         : Isiah
Name              : Isiah.Jesus
```

Answer:
```
Isiah.Jesus
```

# 4. (15)
Prompt:
```
Continue to follow the insider trail to find additional insider threats and their compromised mission. This flag is a video link.
```

Steps:
```
PS C:\> Get-ADUser -Filter {Name -eq "Isiah.Jesus"} -Properties *

StreetAddress                        : aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g/dj1kUXc0dzlXZ1hjUQ==

Base64:
https://www.youtube.com/watch?v=dQw4w9WgXcQ
```

Answer:
```

```
