# Linux Basics Bash Logic

# 1. (10)
Prompt:
```
Directory: home/garviel/Battlefield/

The garviel user has a minefield map and controls to a Titan War Machine located in their home directory. Interpret the Titan Controls to navigate the minefield and annihilate the target.

Enter the correct movement codes to make the Titan obliterate the target.

Format: XXX3X2X......
```

Steps:
```bash
Enter the Command Sequence for the Titan: AAAAA3AAA3AAAABAABAAAA
Step Forward Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Turn Right Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Turn Right Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Turn Left Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Turn Left Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Step Forward Command Accepted
Target Obliterated
```

Answer:
```
AAAAA3AAA3AAAABAABAAAA
```

# 2. (10)
Prompt:
```
The flag resides in $HOME/paths... you just need to determine which flag it is. The flag sits next to a string matching the name of a $PATH/binary on your system.

Hint: The correct binary is not echo
```

Steps:
```bash
for b in $(ls /usr/bin); do cat paths | grep "^$b" ; done
python3    flag:{  Vrc0vw7ZUaLBpQp  }
```

Answer:
```
Vrc0vw7ZUaLBpQp
```
