# Linux File System Commands and Log Filtering

## 1. Navigating and inspecting files

Analysts spend a lot of time moving through directories and reading configuration files or text-based logs in Bash.

| Command | Purpose | Example |
|---|---|---|
| `pwd` | Print working directory (shows current path) | `pwd` |
| `ls` | List files and directories (`-l` detailed, `-a` hidden files) | `ls -la /var/log` |
| `cd` | Change current directory | `cd /etc/ssh` |
| `cat` | Display the full contents of a small file | `cat /etc/hostname` |
| `head` | Display the first 10 lines of a file (`-n` sets line count) | `head -n 20 auth.log` |
| `tail` | Display the last 10 lines of a file (`-f` follows live updates) | `tail -n 25 auth.log` |
| `less` | View a large file one page at a time (`q` to quit) | `less /var/log/syslog` |

## 2. Creating, moving, and removing files

| Command | Purpose | Example |
|---|---|---|
| `mkdir` | Create a new directory | `mkdir incident_notes` |
| `touch` | Create an empty file or update a file's timestamp | `touch timeline.txt` |
| `cp` | Copy a file or directory (`-r` for directories) | `cp sshd_config sshd_config.bak` |
| `mv` | Move or rename a file or directory | `mv draft.txt final_report.txt` |
| `rm` | Remove a file (`-r` removes directories recursively) | `rm old_temp.txt` |

Use `rm -r` carefully, because Linux does not move deleted files from the command line into a recycle bin.

## 3. Searching and filtering with `find` and `grep`

Text logs on Linux servers can contain thousands of lines. Combining `find` and `grep` helps narrow down relevant indicators.

- **`find`:** Searches for files and directories by name, type, owner, size, or modification time.
- **`grep`:** Searches inside file contents or piped text for matching strings or patterns.

```bash
# Find all .log files inside /var/log
find /var/log -name "*.log"

# Search for failed SSH login attempts (case-insensitive with -i)
grep -i "failed password" /var/log/auth.log

# Search recursively (-r) across /etc for a specific IP address
grep -rn "198.51.100.25" /etc/

# Count (-c) how many times an IP appears in a web access log
grep -c "203.0.113.44" access.log
```

## 4. Getting help in the shell

Linux includes built-in documentation so analysts can check unfamiliar command flags without leaving the terminal:

```bash
# Open the full manual page for grep
man grep

# Display a quick summary of flags for chmod
chmod --help

# Search manual page descriptions by keyword
apropos permission
```

## 5. Simulated log filtering example

This example uses fictional log lines with RFC 5737 documentation IP addresses:

```text
Nov 12 08:11:04 web01 sshd[2104]: Failed password for invalid user admin from 203.0.113.88 port 49812 ssh2
Nov 12 08:11:07 web01 sshd[2104]: Failed password for invalid user admin from 203.0.113.88 port 49814 ssh2
Nov 12 08:12:19 web01 sshd[2119]: Accepted publickey for deploy from 198.51.100.14 port 51200 ssh2
```

Running `grep "Failed password" sample_auth.log` filters out the normal `Accepted publickey` session and isolates the two failed login lines from `203.0.113.88` for further review.

## 6. Key point

Pairing navigation commands (`ls`, `cd`, `tail`) with `find` and `grep` lets an analyst locate log files and isolate suspicious events directly from the shell.

## References

- [GNU Grep Manual](https://www.gnu.org/software/grep/manual/)
- [GNU Findutils Manual](https://www.gnu.org/software/findutils/manual/)
