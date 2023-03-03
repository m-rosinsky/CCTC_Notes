# Linux Boot Bits and Bytes

# 1. (5)
Prompt:
```
How many bits are in a nibble, and a byte?

Flag format: #,#
```

Answer:
```
4,8
```

# 2. (5)
Prompt:
```
How many bits does a single Hexadecimal character represent?
```

Answer:
```
4
```

# 3. (5)
Prompt:
```
Each hex digit contains a value of 8 bits when used to represent memory.

How many bytes could the range 0x00000000 - 0x00000010 contain?
```

Answer:
```
17
```

# 4. (10)
Prompt:
```
Execute : sudo cat /dev/vda | xxd -l 32 -c 0x10 -g 1

What are the values contained in hex positions 0x00000001 through 0x00000008?

Flag format: Value,Value,Value

Machine: For this challenge: Minas_Tirith (ssh from Admin_Station)
```

Answer:
```
63,90,8e,d0,31,e4,8e,d8
```
