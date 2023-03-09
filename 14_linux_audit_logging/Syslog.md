# Linux Auditing and Logging Syslog

# 1. (5)
Prompt:
```
Download the attached rsyslog configuration file for the Syslog # challenges.

In the legacy rules section of the file, what facility is logged to 0.log?
```

Answer:
```
kernel
```

# 2. (5)
Prompt:
```
In the legacy rules section of the file, how many severities are logged to 0.log?

Flag: Total number of severities
```

Answer:
```
8
```

# 3. (5)
Prompt:
```
In the legacy rules section of the file, how many severities are logged to 4min.log?

List the severities from highest severity (lowest numerical listed) to lowest severity (highest numerical listed) using their severity name.

Flag format: name,name,name
```

Answer:
```
emergency,alert,critical,error,warning
```

# 4. (5)
Prompt:
```
In the legacy rules section of the file, how many severities are logged to 4sig.log?

List the severities from highest severity (lowest numerical listed) to lowest severity (highest numerical listed), using their severity name.

Flag format: name,name,name

Hint: I’m sure they made a man page for this. Read the downloaded file for some links.
```

Answer:
```
notice,informational,debug
```

# 5. (5)
Prompt:
```
What is being logged in not.log?

Provide the facilities from lowest facility to highest facility numerically, and the severity being logged. (List only the first word for each.)

Flag format: facility,facility,facility,severity
```

Answer:
```
mail,clock,ntp,notice
```

# 6. (5)
Prompt:
```
What facilities and what severities are being sent to a remote server over a reliable connection using port 514?

Provide the facility names, number of severities, and the correct destination IP address.

Flag format: F,F,#,IP
```

Answer:
```
auth,authpriv,8,10.30.0.1
```

# 8. (5)
Prompt:
```
What messages are being sent to 10.84.0.1?

Provide the facility number, the number (amount) of severity codes, and Layer 4 connection type as the answer.

Flag format: F,S,Layer 4 connection Type
```

Answer:
```
0,7,UDP
```

# 9. (5)
Prompt:
```
Which cron log severity code is saved only to the local machine?

Flag format: #

(Continue to reference your 50-cctc.conf file from Syslog1)
```

Answer:
```
7
```

# 10. (5)
Prompt:
```
The emergency messages (only) on the system are sent to what IP Address?

(Continue to reference your 50-cctc.conf file from Syslog1)
```

Answer:
```
10.24.0.1
```
