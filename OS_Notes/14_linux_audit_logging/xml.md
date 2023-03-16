# Linux Auditing and Logging XML

# 1. (5)
Prompt:
```
File: /home/garviel/output.xml

Identify the XML element name in the output below

<scaninfo type="syn" protocol="tcp" numservices="200" services="1-200"/>
```

Answer:
```
<scaninfo/>
```

# 2. (5)
Prompt:
```
Identify one of the XML attributes in the output below

<scaninfo type="syn" protocol="tcp" numservices="200" services="1-200"/>

Flag format: value="pair"
```

Answer:
```
type="syn"
```

# 3. (10)
Prompt:
```
File: /home/garviel/output.xml

Parse all of the IP addresses from the file using XPATH queries

https://www.w3schools.com/xml/xpath_intro.asp

HINT:

    http://xpather.com/
    http://www.whitebeam.org/library/guide/TechNotes/xpathtestbed.rhtm
```

Steps:
```
garviel@terra:~$ xpath -q -e //@addr output.xml | md5sum
```

Answer:
```
0e850f14fc192c5105955ec094287bd2
```

# 4. (10)
Prompt:
```
File: /home/garviel/output.xml

    Select all of the IP addresses and ports using a single XPATH Union Statement

    Pipe the result to md5sum for the flag

HINT:

    https://librarycarpentry.org/lc-webscraping/02-xpath/index.html
```

Steps:
```
garviel@terra:~$ xpath -q -e '//@addr|//@portid' output.xml | md5sum
```

Answer:
```
ff7990139b6d09aa65afb6e069db0dec
```

# 5. (15)
Prompt:
```
File: /home/garviel/output.xml

    Select every IP address with open (in use) ports using XPATH queries and XPATH axes.

    Pipe the result to md5sum for the flag
```

Steps:
```
<port protocol="tcp" portid="22"><state state="open" reason="syn-ack" reason_ttl="126"/><service name
="ssh" method="table" conf="3"/></port>

garviel@terra:~$ xpath -q -e "//state[@state='open']/../../..//@addr|//state[@state='open']/../@porti
d" output.xml | md5sum
ef0acbb3e9a376395d35c4ad9e9418ba  -
```

Answer:
```
ef0acbb3e9a376395d35c4ad9e9418ba
```
