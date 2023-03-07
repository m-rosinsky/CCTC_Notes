# Linux Process Validity

Start Key: `start1640`

# 1. Process Listing

A process refers to a program in execution.

## 1.1 The PS Command

Info read from the virtual files in the `/proc` directory.

```bash
garviel@terra:~$ ps
  PID TTY          TIME CMD
 3515 pts/0    00:00:00 bash
 3544 pts/0    00:00:00 ps
```

## 1.2 The Top Command

Provides a dynamic real-time view of the running processes.

```bash
top - 13:16:30 up 13 days, 16:13,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  88 total,   1 running,  49 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.4 sy,  0.0 ni, 99.6 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  4039268 total,  2018596 free,   114872 used,  1905800 buff/cache
KiB Swap:        0 total,        0 free,        0 used.  3634548 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S %CPU %MEM     TIME+ COMMAND                           
    1 root      20   0  159848   6624   4152 S  0.0  0.2   0:14.54 systemd
    2 root      20   0       0      0      0 S  0.0  0.0   0:00.05 kthreadd
    4 root       0 -20       0      0      0 I  0.0  0.0   0:00.00 kworker/0:0H
    6 root       0 -20       0      0      0 I  0.0  0.0   0:00.00 mm_percpu_wq
    7 root      20   0       0      0      0 S  0.0  0.0   0:01.63 ksoftirqd/0
    8 root      20   0       0      0      0 I  0.0  0.0   0:01.33 rcu_sched
    9 root      20   0       0      0      0 I  0.0  0.0   0:00.00 rcu_bh
```

Press `shift + v` to view processes in hierarchical view.

## 1.3 The Htop Command

`htop` is used to display various info about processes dynamically.

# 2. Startup Processes

Executing the `ps` command with the `-elf` argument will have full formatting
of all running processes.

```bash
garviel@terra:~$ ps -elf
F S UID        PID  PPID  C PRI  NI ADDR SZ WCHAN  STIME TTY          TIME CMD
4 S root         1     0  0  80   0 - 39962 -      Feb21 ?        00:00:14 /sbin/init       
1 S root         2     0  0  80   0 -     0 -      Feb21 ?        00:00:00 [kthreadd]       
1 I root         4     2  0  60 -20 -     0 -      Feb21 ?        00:00:00 [kworker/0:0H]   
1 I root         6     2  0  60 -20 -     0 -      Feb21 ?        00:00:00 [mm_percpu_wq]   
1 S root         7     2  0  80   0 -     0 -      Feb21 ?        00:00:01 [ksoftirqd/0]    
1 I root         8     2  0  80   0 -     0 -      Feb21 ?        00:00:01 [rcu_sched]      
1 I root         9     2  0  80   0 -     0 -      Feb21 ?        00:00:00 [rcu_bh]
```

```
F:      Field Table
S:      Current status of the process
UID:    The effective user ID of the process's owner
PID:    Process ID
PPID:   The parent process's ID
C:      The processor utilization for scheduling. This field is not displayed when the -c option is used
PRI:    The kernel thread's scheduling priority. Higher numbers mean higher priority
NI:     The process's nice number, which contributes to its scheduling priority. Making a process "nicer" means lowering its priority
ADDR:   The address of the proc structure
SZ:     The virtual address size of the process
WCHAN:  The address of an event or lock for which the process is sleeping
STIME:  The starting time of the process (in hours, minutes, and seconds)
TTY:    The terminal from which the process (or its parent) was started. A question mark indicates there is no controlling terminal
TIME:   The total amount of CPU time used by the process since it began
CMD:    The command that generated the process
```

#### Key points

- All kernel processes are forked from `[kthreadd]`
- All user processes are forked from `/sbin/init` or direct ancestor
- Kernel processes can be identified from being enclosed in `[]`
- Processes spawned from `[kthreadd]` will have `PPID` of `2`
- Processes spawned from `/sbin/init` will have `PPID` of `1`

# 3. Concepts of Virtual Memory

Virtual memory is divided into kernel space and user space

## 3.1 Kernel Space

- Kernel processes will run in the kernel space of virtual memory
- Code running in this space has _unrestricted access_ to the processor and main memory
- Kernel space can be accesses by user processes through the use of syscalls

## 3.2 User Space

- User mode restricts access to a small subset of memory and safe CPU operations

## 3.3 OS Protection

| ![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/010_linux_process_validity/pages/OS_Protection_Ring.png "Linux OS Protection") |
|:--:|

- OS protection improves fault tolerance and provides computer security

# 4. Process Ownership, EUID, RUID, and UID

- A user entity can run processes and own files

## 4.1 Process Ownership

- `/sbin/init` or `/lib/systemd/systemd` always have a PID of 1
- Users of the system may be:
    - Human users - People who log in to the system
    - System users - non-interactive background services such as databases

```bash
# Show range of User IDs for system and human users
garviel@terra:~$ grep UID /etc/login.defs
UID_MIN                  1000
UID_MAX                 60000
#SYS_UID_MIN              100
#SYS_UID_MAX              999
```

## 4.2 Effective User ID (EUID)

Defines the access rights for a process.

## 4.3 Real User ID (RUID)

Defines who can interact with a running process, and who can send signals to it.

```bash
# Viewing special permissions on passwd executables
garviel@terra:~$ ls -l /usr/bin/passwd
-rwsr-xr-x 1 root root 59640 Nov 29 12:25 /usr/bin/passwd
```

# 5. System Calls

| ![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/010_linux_process_validity/pages/linproc1.png "Process Spawning") |
|:--:|

## 5.2 Linux Signals

```bash
garviel@terra:~$ kill -l
 1) SIGHUP       2) SIGINT       3) SIGQUIT      4) SIGILL       5) SIGTRAP    
 6) SIGABRT      7) SIGBUS       8) SIGFPE       9) SIGKILL     10) SIGUSR1    
11) SIGSEGV     12) SIGUSR2     13) SIGPIPE     14) SIGALRM     15) SIGTERM    
16) SIGSTKFLT   17) SIGCHLD     18) SIGCONT     19) SIGSTOP     20) SIGTSTP    
21) SIGTTIN     22) SIGTTOU     23) SIGURG      24) SIGXCPU     25) SIGXFSZ    
26) SIGVTALRM   27) SIGPROF     28) SIGWINCH    29) SIGIO       30) SIGPWR     
31) SIGSYS      34) SIGRTMIN    35) SIGRTMIN+1  36) SIGRTMIN+2  37) SIGRTMIN+3
38) SIGRTMIN+4  39) SIGRTMIN+5  40) SIGRTMIN+6  41) SIGRTMIN+7  42) SIGRTMIN+8
43) SIGRTMIN+9  44) SIGRTMIN+10 45) SIGRTMIN+11 46) SIGRTMIN+12 47) SIGRTMIN+13
48) SIGRTMIN+14 49) SIGRTMIN+15 50) SIGRTMAX-14 51) SIGRTMAX-13 52) SIGRTMAX-12
53) SIGRTMAX-11 54) SIGRTMAX-10 55) SIGRTMAX-9  56) SIGRTMAX-8  57) SIGRTMAX-7
58) SIGRTMAX-6  59) SIGRTMAX-5  60) SIGRTMAX-4  61) SIGRTMAX-3  62) SIGRTMAX-2
63) SIGRTMAX-1  64) SIGRTMAX

# Send SIGINT to process
kill -2 <PID>
```

# 6. Foreground and Background Processes

## 6.1 Orphan Processes

- Orphan process has a parent who is terminated and is adopted by `sbin/init` (PPID = 1)

```bash
# Close a shell/terminal and force all children to be adopted
disown -a && exit
```

## 6.2 Zombie (Defunct) Processes

Processes that have completed execution but have not been reaped by parent processes

## 6.3 Daemons

- Processes that run in the background that are intentionally orphaned.
- Parent process is 1, so shutdown would be required to kill process.

```bash
# See process with ppid of 1 (/sbin/init)
ps --ppid 1 -lf
```

### 6.3.1 Interacting with Linux Services

The basic object that `systemd` manages is a `unit`.

```bash
# List services
systemctl --type=service

systemctl list-unit

# Get status of service
systemctl status <pid or name>

# Interact
systemctl <start / stop / restart> <pid or name>
```

## 6.4 Job Control

Job status are foreground, background, and stop.

```bash
# Run command in background with &
ping 8.8.8.8 &

# Stop the job with ^Z
```

## 6.5 Cron Jobs

Jobs that run repeatedly on a fixed schedule. Usually used for auto system maintenance

Cron daemon checks `/var/spool/cron`, `/etc/cron.d`, and `/etc/crontab` once a minute.

Two types of cron jobs:
1. System cron jobs
    - Run as root and rigidly scheduled
    - controlled by `/etc/crontab`
2. User cron Jobs
    - Stored in `/var/spool/cron/crontabs`

```bash
# Load crontab data from specified file
crontab -u [user] file

# Display user's crontab contents
crontab -l -u [user]

# Remove user crontab contents
crontab -r -u [user]

# Edit user crontab contents
crontab -e -u [user]
```

Examples:
```
* Run backup everyday at 0412
** `12 4 * * *`    /usr/bin/backup
```

```bash
sudo lsof | head
```

# 7. Processes and Proc Dir

- The `/proc` directory contains hierarchy of special files which allow users to see processes
- Every process access files called fds.

## 7.1 File Descriptors

- Unique handles for a file, such as open files, pipes, sockets, etc.

### 7.1.1 Viewing File Descriptors

```bash
# See all open files for a specified process
sudo lsof -c sshd
```
