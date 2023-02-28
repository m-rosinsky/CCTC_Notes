# Windows Registry

Start Key: `start357`

## 1. Primer_Registry_1 (1)

Prompt:
```
What Windows registry path is the Volatile Hive?

Research: https://vistech.net/~champ/online-docs/books/mwin2reg/ch11-30975.html
```

Answer:
```
HKLM\HARDWARE
```

## 2. Primer_Registry_2 (1)

Prompt:
```
What registry key creates the Wow6432Node to represent 32-bit applications that run on a 64-bit version of Windows?

Research: https://learn.microsoft.com/en-us/troubleshoot/windows-client/application-management/wow6432node-registry-key-present-32-bit-machine
```

Answer:
```
HKEY_LOCAL_MACHINE\SOFTWARE
```

## 3. Primer_Registry_3 (1)

Prompt:
```
In what registry path are the BOOT_START drivers located?

Research: https://learn.microsoft.com/en-us/windows-hardware/drivers/install/hklm-system-currentcontrolset-services-registry-tree
```

Answer:
```
HKLM\SYSTEM\CurrentControlSet\Services
```

## 4. Primer_Registry_4 (1)

Prompt:
```
What start value do BOOT_START drivers have in the registry?

Research: https://learn.microsoft.com/en-us/windows-hardware/drivers/install/specifying-driver-load-order
```

Answer:
```
0x0
```

## 5. Primer_Registry_5 (1)

Prompt:
```
During kernel initialization, what registry location is read containing all SYSTEM_START drivers and services with a start value of 0x1?

Research: https://learn.microsoft.com/en-us/windows-hardware/drivers/install/hklm-system-currentcontrolset-services-registry-tree
```

Answer:
```
HKLM\SYSTEM\CurrentControlSet\Services
```

## 6. Primer_Registry_6 (1)

Prompt:
```
Auto_START drivers and services are loaded after kernel initialization. What start value do they have in the registry?

Research: https://learn.microsoft.com/en-us/windows-hardware/drivers/install/specifying-driver-load-order
```

Answer:
```
0x02
```

## 7. Primer_Registry_7 (1)

Prompt:
```
What start value do DEMAND_START drivers and services have in the registry?

Research: https://learn.microsoft.com/en-us/windows-hardware/drivers/install/specifying-driver-load-order
```

Answer:
```
0x3
```

## 8. Primer_Registry_8 (1)

Prompt:
```
When accessing a remote registry which are the only 2 accessible HKEYs?

SYNTAX Hive, Hive

Research: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg-load
```

Answer:
```
HKLM, HKU
```

## 9. Primer_Registry_9 (1)

Prompt:
```
What PowerShell cmdlet will list currently mapped drives?

Research: https://learn.microsoft.com/en-us/powershell/scripting/samples/managing-windows-powershell-drives?view=powershell-7.2
```

Answer:
```
Get-PSDrive
```

## 10. Primer_Registry_10 (1)

Prompt:
```
What is the native Windows GUI tool for managing the registry?

Research: https://support.microsoft.com/en-us/windows/how-to-open-registry-editor-in-windows-10-deab38e6-91d6-e0aa-4b7c-8878d9e07b11
```

Answer:
```
Regedit
```
