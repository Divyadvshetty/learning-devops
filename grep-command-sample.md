I'll give you **one complete&#x20;**`file.txt`**&#x20;practice file** that contains usernames, errors, debug messages, dates, IP addresses, file paths, comments, empty lines, SSH failures and more.

You can use this single file to practise most of your 25+ grep examples (including the advanced ones).

## **Step 1: Create your practice directory**

Open Ubuntu terminal and run:

```
mkdir -p ~/linux-training/grep-lab
cd ~/linux-training/grep-lab
```

## **Step 2: Create&#x20;**`file.txt`

Copy and paste this complete command into your Ubuntu terminal:

```

cat > file.txt <<'EOF'
# Linux Grep Practice File
# User information and system logs

user alice
user bob
user guest
admin root
User Divya
OLD password detected
old configuration found
This is an old backup file

error: database connection failed
debug: checking server status
status: server running
error: authentication failed
debug: user login successful
status: active

Failed password for alice
Failed password for bob
SSH login successful for user
Connection failed from 192.168.1.50
Request received from 192.168.1.100

Date: 2026-11-19
Year: 2025
Employee ID: 1234
Port number: 8080
Server code: 500

/home/student/bin/python
/etc/ssh/sshd_config
/var/log/syslog
/home/student/config/app.conf

#!/bin/bash
# TODO: Fix login error
# TODO: Update server configuration

def authenticateUser():
    print("User authenticated")

import requests

# End of file
EOF

```

## **Step 3: Check your file**

```
cat file.txt
```

You should see all the sample data, including blank lines.

## **Step 4: Run your 25 grep examples**

Try these directly:

```

# 1. Search exact string
grep "user" file.txt

# 2. Case-insensitive
grep -i "old" file.txt

# 3. Whole word
grep -w "old" file.txt

# 4. Exact full line
grep -x "# End of file" file.txt

# 5. Multiple patterns
grep -e "error" -e "debug" file.txt

# 6. Invert match
grep -v "user" file.txt

# 7. Remove comments and empty lines
grep -v -e "^#" -e "^$" file.txt

# 8. Count matching lines
grep -c "user" file.txt

# 9. Show only numbers
grep -o "[0-9]\+" file.txt

# 10. Stop after 2 matches
grep -m 2 "user" file.txt

# 11. Show line numbers
grep -n "failed" file.txt

# 12. Two lines after match
grep -A 2 "error" file.txt

# 13. Two lines before match
grep -B 2 "status" file.txt

# 14. One line before and after
grep -C 1 "debug" file.txt

# 15. Highlight matching text
grep --color=always "admin" file.txt

# 16. Lines starting with user
grep "^user" file.txt

# 17. Lines ending with bash
grep "bash$" file.txt

# 18. Four-digit numbers
grep -E "[0-9]{4}" file.txt

# 19. Alice or Bob
grep -E "alice|bob" file.txt

# 20. File paths
grep -E "/[a-z]+/[a-z]+" file.txt

```

## **Step 5: Practise examples 21–25**

First, create two additional text files to practise searching multiple files:

```
echo "Python programming practice" > notes.txt
echo "Linux administration practice" > clean.txt
```

Now run:

```

# 21. Show filenames containing failed
grep -l "failed" *.txt

# 22. Show filenames without failed
grep -L "failed" *.txt

# 23. Search recursively
grep -r "alice" .

# 24. Suppress error messages
grep -s "alice" file.txt missing.txt

# 25. Filter using pipe
cat file.txt | grep "user" | grep -v "guest"

```

## **Step 6: Practise advanced examples 26–45**

Some of these require additional files or actual Linux services.

Create a sample project:

```
mkdir -p project/src
```

```
cat > project/src/app.py <<'EOF'
import requests

# TODO: Improve authentication
def authenticateUser():
    print("Login successful")

server_ip = "192.168.1.50"
EOF
```

Now practise:

```

# Find a specific function
grep -rnw project -e 'authenticateUser'

# Find TODO comments
grep -rn --exclude-dir=.git "TODO" .

# Search Python files only
grep -rn --include="*.py" "import requests" .

# Find IP addresses
grep -rnE "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}" project/

```

## **Step 7: Practise real Linux system commands**

These commands search actual system information rather than your sample `file.txt`.

| No. | Command                                            | What it checks            |
| --- | -------------------------------------------------- | ------------------------- |
| 27  | `ps aux \\| grep nginx`                            | Nginx process             |
| 28  | `ss -tulnp \\| grep 8080`                          | Port 8080                 |
| 29  | `dpkg -l \\| grep python3`                         | Installed Python packages |
| 30  | `rpm -qa \\| grep openssl`                         | RHEL package list         |
| 31  | `lsusb \\| grep -i keyboard`                       | USB keyboard              |
| 32  | `grep -i error /var/log/syslog`                    | System errors             |
| 33  | `tail -f /var/log/nginx/access.log \\| grep "500"` | Live server errors        |
| 34  | `grep "Failed password" /var/log/auth.log`         | Failed SSH logins         |
| 35  | `grep -c "192.168.1.50" /var/log/nginx/access.log` | IP request count          |
| 36  | `grep -C 5 "panic" /var/log/kern.log`              | Kernel panic context      |

Some files and services may not exist on your Ubuntu system. For example, Nginx logs require Nginx to be installed and running.

## **Step 8: More useful configuration commands**

```
# View SSH settings without comments and blank lines
grep -vE "^#|^$" /etc/ssh/sshd_config

# Check CPU model
grep "model name" /proc/cpuinfo | head -n 1

# Check total RAM
grep "MemTotal" /proc/meminfo
```

## **Your learning target**

45 examples

Practise in this order:

1. Basic searching (1–10).
2. Line numbers and context (11–15).
3. Regular expressions (16–20).
4. Multiple files and pipes (21–25).
5. System and DevOps commands (27–36).
6. Codebase searching and configuration files (43–45).

**Important:** You don't need to memorise all 45 commands in one day. Understand what each option (`-i`, `-v`, `-n`, `-c`, `-r`, `-E`, `-A`, `-B`, `-C`) does.

My suggestion: Run the first five commands and send me your Ubuntu terminal screenshot. I'll explain your actual output line by line.
