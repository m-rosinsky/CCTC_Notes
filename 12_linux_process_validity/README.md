# Linux Process Validity

Start Key: `start`

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
