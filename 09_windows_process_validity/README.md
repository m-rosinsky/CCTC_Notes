# Windows Process Validity

Start Key: `start`

# 1. What is Process Validity and Why it Matters

## 1.1 What is Process Validity?

- Validating processes as good or bad from attrs and characteristics
- Malware can hide in processes, or hook into legitimate ones

# 2. Processes, DLLs, and Services

# 2.1 What are they?

- Processes can be run by a user, or run in the background

- What is a DLL?
	- Dynamic Link Library
	- Cannot be directly executed, dependent on an EXE to use as an entry point.

	- Examples:
		- Comdlg32
		- Device drivers
		- ActiveX Controls

	- Documentation:
		- https://learn.microsoft.com/en-us/troubleshoot/windows-client/deployment/dynamic-link-library

- What is a Service?
	- Long running execs that run in their own Windows sessions
		- Can be set to auto start on boot
		- Can be paused and resumed
		- No interface with user

	- Documentation:
		- https://learn.microsoft.com/en-us/dotnet/framework/windows-services/introduction-to-windows-service-applications

## 2.2 How to View Processes and DLLs

### 2.2.1 View Processes in PowerShell:
```powershell
# General command to get processes running
Get-Process

# Sort Processes by their IDs
Get-Process | Sort -Property Id | more

# Only show certain process properties
Get-Process | Select Name, ID, Description | Sort -Property Id | more

# View only certain processes
Get-Process | SMSS,CSRSS,LSASS | Sort -Property Id

# View modules/DLLs used by defined processes and their file locations
Get-Process chrome | foreach {$a} {$_.modules} | more

# View only mods/DLLs used by Chrome with "chrome" in their name and file locations.
Get-Process chrome | foreach {$a} {$_.modules} | Where-Object ModuleName -like '*chrome*' | more
```

Powershell Ciminstance
```powershell
# View processes with PPID
Get-CimInstance Win32_Process

# View additional properties
Get-CimInstance Win32_Process | Get-Member

# View processes with PID and PPID sorted by PID
Get-CimInstance Win32_Process | select name,ProcessId,ParentProcessId | sort processid

# View an instance of all Win32 services
Get-Ciminstance Win32_service | Select Name, Processid, Pathname | more
```

### 2.2.2 View Processes in CMD:
```cmd
tasklist | more

# Verbose
tasklist /v

# Service info for each process without trunaction
tasklist /svc

# Display mods/DLLs associated with all processes
tasklist /m | more

# Display mods/DLLs associated with a specific process
tasklist /m /fi "IMAGENAME eq chrome.exe" | more

# Formatting options
tasklist /fo:table | more
```

### 2.2.3 View Processes in the GUI

- Task Manager
- `Procexp.exe` (sysinternals)

## 2.3 How to View Services

### 2.3.1 View Services in PowerShell
```powershell
# View only system services and display certain properties
Get-CimInstance Win32_service | Select Name, Processid, Pathname | more

# View all services
Get-Service | more

# View a defined service in list format
Get-Service ALG | format-list *

# View only currently running services
Get-Service | Where-Object {$_.Status -eq "Running"} | more
```

### 2.3.2 View Services in CMD
```cmd
# View Services
sc query | more

# View extended info for all services
sc queryex type=service

# View extended info for all inactive services
sc queryex type=service state=inactive

# Additional examples of the SC command
sc /?						# basic enumeration
sc qc						# Config info for a service
sc queryex eventlog			# Info for the eventlog service including PID
sc qdescription eventlog 	# Query eventlog service desc
sc qc eventlog				# Show the binary command that loads the service
sc showsid eventlog			# Displays the service SID and status
sc enmudepend				# Lists the services that cannot run unless specified serv running

# View all running services
net start
```

### 2.3.3 View Services in the GUI

- `services.msc`
- `PsService` (sysinterals)

# 3. Scheduled Tasks

## 3.1 What are Scheduled Tasks?

- Launch programs when defined conds are met
	- Preset time
	- On boot
	- User log in

- Easy way to hide malware that can invoke itself

## 3.2 How to View Scheduled Tasks

### 3.2.1 View Scheduled Tasks in PowerShell
```powershell
# View all properties of the first scheduled task
Get-ScheduledTask | Select * | Select -First 1
```

### 3.2.2 View Scheduled Tasks in CMD
```cmd
schtasks /query /tn "IchBinBosh" /v /fo list
```

### 3.2.3 View Scheduled Tasks in GUI

- Task Scheduler
- `autoruns` (sysinternals)

### 3.2.4 Autorun Registry Locations

- Local Machine
	- `HKLM\Software\Microsoft\Windows\CurrentVerstion\Run`
	- `HKLM\Software\Microsoft\Windows\CurrentVerstion\RunOnce`
	- `HKLM\System\CurrentControlSet\Services`

- Current User
	- `HKCU\Software\Microsoft\Windows\CurrentVerstion\Run`
	- `HKCU\Software\Microsoft\Windows\CurrentVerstion\RunOnce`

- The order in which services are loaded can be adjusted
	- `HKLM\System\CurrentControlSet\Control\ServiceGroupOrder`
	- `HKLM\CurrentControlSet\Control\GroupOrderList`

## 3.3 DEMO: Create Task to open listening port via the PowerShell Process

### 3.3.1 Create IchBinBosh task

- Opens port listening on 6666 every 15 mins
```cmd
schtasks /Create /TN IchBinBosh /SC MINUTE /MO 15 /TR "powershell.exe -win hidden -encode JABMAD0ATgBlAHcALQBPAGIAagBlAGMAdAAgAFMAeQBzAHQAZQBtAC4ATgBlAHQALgBTAG8AYwBrAGUAdABzAC4AVABjAHAATABpAHMAdABlAG4AZQByACgANgA2ADYANgApADsAJABMAC4AUwB0AGEAcgB0ACgAKQA7AFMAdABhAHIAdAAtAFMAbABlAGUAcAAgAC0AcwAgADYAMAA="
```

```powershell
$command = '$L=New-Object System.Net.Sockets.TcpListener(6666);$L.Start();Start-Sleep -s 60'
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

### 3.3.2 Confirm IchBinBosh Exists and View Properties

CMD
```cmd
schtasks /query | select-string -pattern IchBinBosh -Context 2,4
```

PowerShell
```powershell
Get-ScheduledTask | Select * | select-string -pattern IchBinBosh -Context 2,4
```

GUI

- Show in either Task Scheduler or `Autoruns`

# 4. Network Connections

## 4.1 View Network Connections in PowerShell
```powershell
# Show all connections in established state
Get-NetTCPConnection -State Established
```

## 4.2 View Network Connections in CMD
```cmd
# Show netstat help
netstat /?

# Display all TCP/UDP connections with ports
netstat -anob | more
```

## 4.3 View Network Connections in the GUI

- `TCPView` (sysinternals)

# 5. Identifying Abnormalities/Suspicious Activity

- Mispellings in services/process list
- Directory of process is usually `C:\Windows\System32`
- Third party process run elsewhere
	- Ex. Chrome runs from `C:\Program Files`
- Processes have non-standard listening ports
- Multiple process using same name that should be unique
- Handles or DLLs a process is using
	- DLL Hijacking