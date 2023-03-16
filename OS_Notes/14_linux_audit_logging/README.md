# Linux Auditing and Logging

Start Key: `start2021`

# 1. What is Logging?

- A record or performance, events, or day-to-day activities

# 2. Linux Logging Daemons

- Logging controlled by `syslog` (RFC 5424) or `journald` (Linux unique)
- Both stored in `/var/log/`

# 3. Syslog Daemon

- Stored in text documents within `/var/log`
- Configured using files in `/etc/rsyslog`

- Syslog logging config standard:
    - Selectors: `facility.severity`
    - Action: `/path/to/log/location`

    - `Facility`: the source, or event, that generated the log
    - `Severity`: how urgent an event is (0 - 7) with 0 being emergency
    - `/path/to/log/location`: where the log is stored and any action taken on event before storage

| Numerical Code | Facility |
| 0 | kernel messages |
| 1 | user-level messages |
| 2 | mail system |
| 3 | system daemons |
| 4 | security / auth messages |
| 5 | messages made by syslogd |
| 6 | line printer system |
| 7 | network news subsystem |

| Numerical Code | Severity |
| 0 | Emergency |
| 1 | Alert |
| 2 | Critical |
| 3 | Error |
| 4 | Warning |
| 5 | Notice |
| 6 | Info |
| 7 | Debug |

```bash
cat /etc/rsyslog.d/50-default.conf
```

## 3.1 Filtering Syslog Log Files

```bash
grep timesyncd /var/log/syslog

# Can also do regex
grep -R "regex_string" /var/log/syslog
```

## 3.2 Log Rotations

- Daily cronjob runs the `logrotate` binary
- Has path to `/etc/logroatate.conf`

```bash
ls -l /var/log
```

## 3.3 Essential Syslog Types/Locations

### 3.3.1 Authentication

- `/var/log/auth.log`: Authentication related events
- `/var/run/utmp`: Users current logged in (use `last` command)
- `/var/log/wtmp`: History file for utmp (`last`)
- `/var/log/btmp`: Failed login attempts

### 3.3.2 Application

- Anything to do with programs

### 3.3.3 System

- `/var/log/messages`: Legacy catchall
- `/var/log/syslog`: Ubuntu/Debian catchall
- `dmesg`: Device Messenger

### 3.3.4 Logging at a Glance

- All logs are in `/var`, most are in `/var/log`
- Config: `/etc/rsyslog.conf`
- Service: `/usr/sbin/rsyslogd`

# 4. Journald Logs
