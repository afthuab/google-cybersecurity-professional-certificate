# Linux Permissions and User Management

## 1. Principle of least privilege on Linux

Linux is a multi-user operating system. Enforcing **least privilege** ensures users and services can only read, modify, or run the files required for their role. Overly broad permissions on configuration files, scripts, or keys can allow privilege escalation.

## 2. Reading file permissions (`ls -l`)

Running `ls -l` displays file type, permissions, owner, group, size, and timestamp:

```text
-rw-r----- 1 root security 2048 Nov 14 09:30 incident_keys.conf
```

The first 10 characters (`-rw-r-----`) break down into four parts:

1. **File type (`-`):** `-` indicates a regular file, `d` indicates a directory, and `l` indicates a symbolic link.
2. **User / Owner (`rw-`):** The file owner (`root`) can read and write, but not execute.
3. **Group (`r--`):** Members of the `security` group can only read the file.
4. **Other (`---`):** All other system users have no access.

| Symbol | Permission | Effect on a file | Effect on a directory |
|---|---|---|---|
| `r` | Read (`4`) | View file contents | List directory contents (`ls`) |
| `w` | Write (`2`) | Modify or overwrite file contents | Create, rename, or delete files inside the directory |
| `x` | Execute (`1`) | Run the file as a program or script | Enter the directory (`cd`) and access its metadata |

## 3. Changing permissions and ownership

- **`chmod` (change mode):** Updates read, write, and execute permissions using either symbolic notation (`u`, `g`, `o`, `a` with `+`, `-`, `=`) or numeric octal notation (`0–7`).
- **`chown` (change owner):** Changes the user owner and/or group owner of a file or directory.

```bash
# Symbolic mode: remove write permission for group and other
chmod go-w report.txt

# Symbolic mode: add execute permission for the file owner
chmod u+x log_parser.sh

# Numeric mode: owner=rwx (7), group=rx (5), other=none (0)
chmod 750 log_parser.sh

# Change owner to analyst1 and group to soc_team
sudo chown analyst1:soc_team alert_notes.txt
```

## 4. User accounts and `sudo`

Linux separates standard user accounts from the privileged `root` superuser account.

- **`sudo` (superuser do):** Allows authorized users to run specific administrative commands with elevated privileges while logging the action for accountability. Using `sudo` for single commands is safer than logging in directly as `root`.
- **`/etc/passwd`:** Stores basic account details (username, UID, GID, home directory, default shell). Readable by all users.
- **`/etc/shadow`:** Stores hashed passwords and password expiration settings. Restricted to `root` / privileged shadow group.

```bash
# Create a new user account with a home directory (-m)
sudo useradd -m analyst2

# Add an existing user to the secondary group 'soc' (-aG preserves existing groups)
sudo usermod -aG soc analyst2

# Delete a user account and remove their home directory (-r)
sudo userdel -r temp_contractor
```

## 5. Key point

Regularly auditing `ls -l` output and tightening permissions with `chmod` and `chown` prevents unauthorized users from reading sensitive data or modifying executable scripts.

## References

- [GNU Coreutils – chmod invocation](https://www.gnu.org/software/coreutils/manual/html_node/chmod-invocation.html)
- [Linux man-pages – sudo(8)](https://man7.org/linux/man-pages/man8/sudo.8.html)
