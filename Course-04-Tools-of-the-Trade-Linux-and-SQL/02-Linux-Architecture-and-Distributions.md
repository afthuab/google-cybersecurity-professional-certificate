# Linux Architecture and Distributions

## 1. Why Linux is widely used in cybersecurity

Linux powers a large share of web servers, cloud workloads, containers, and security appliances. Because it is open source, security teams can audit how it works, customize configurations, and strip out unnecessary components to reduce the attack surface.

## 2. Linux architecture

Linux is organized into distinct layers from physical hardware up to user-facing programs:

| Component | Role |
|---|---|
| Hardware | Physical components such as CPU, memory, disks, and network interfaces |
| Kernel | Core of the OS; manages hardware resources, processes, memory, and device drivers |
| Shell | Command interpreter (such as Bash) that translates user commands into kernel system calls |
| Applications | Utilities, daemons, and user programs running in user space |

## 3. Standard Linux directory structure

Most Linux distributions follow the **Filesystem Hierarchy Standard (FHS)**, starting from the root directory (`/`).

| Directory | Purpose | What an analyst checks here |
|---|---|---|
| `/` | Root of the entire file system | Top-level mount points and directory layout |
| `/bin` and `/usr/bin` | Essential user command binaries (`ls`, `cp`, `grep`) | Unexpected binary modifications or permissions |
| `/etc` | System-wide configuration files | User accounts (`/etc/passwd`), SSH config, firewall rules |
| `/home` | Personal directories for standard users | User scripts, SSH keys (`~/.ssh`), shell history |
| `/var/log` | System, authentication, and service log files | Login attempts (`auth.log` / `secure`), web and kernel logs |
| `/tmp` | Temporary files created by users and applications | Suspicious scripts or payloads dropped by attackers |

## 4. Common Linux distributions

A **Linux distribution (distro)** packages the Linux kernel together with a package manager, system utilities, and default software.

- **Ubuntu:** Beginner-friendly Debian-based distribution widely used on workstations and cloud servers.
- **Debian:** Stable, community-maintained distribution that serves as the base for Ubuntu and Kali Linux.
- **Red Hat Enterprise Linux (RHEL):** Commercial distribution common in enterprise data centers with long-term vendor support.
- **Kali Linux:** Security-focused distribution preloaded with penetration testing, packet analysis, and digital forensics tools.
- **Parrot OS:** Security and privacy-oriented distribution used for vulnerability assessment and defensive testing.

## 5. The Bash shell and standard streams

**Bash (Bourne Again Shell)** is the default command-line shell on many Linux distributions. Commands communicate using three standard data streams:

- **Standard input (`stdin`, descriptor `0`):** Input sent to a command (usually from the keyboard or another command).
- **Standard output (`stdout`, descriptor `1`):** Normal output printed by a command.
- **Standard error (`stderr`, descriptor `2`):** Error messages printed when a command fails.

### Redirection and pipes

```bash
# Redirect standard output to a new file (overwrites existing content)
ls -la /var/log > log_listing.txt

# Append standard output to the end of an existing file
echo "Checked auth logs" >> audit_notes.txt

# Pipe (|) the output of one command into another command for filtering
cat /var/log/auth.log | grep "Failed password"
```

## 6. Key point

Understanding the Linux kernel, shell streams, and standard directories such as `/etc` and `/var/log` helps an analyst locate configuration files and security logs quickly.

## References

- [Linux Filesystem Hierarchy Standard (FHS)](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
- [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/)
