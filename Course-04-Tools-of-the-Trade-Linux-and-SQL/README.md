# Course 04 – Tools of the Trade: Linux and SQL

## Course overview

This course covers foundational operating system concepts, Linux architecture, Bash command-line navigation, file permissions, user management, and querying relational databases with SQL. These tools are used daily in SOC environments to inspect servers, filter text logs, and investigate structured authentication records.

## What I learned

- Explain how operating systems coordinate communication between hardware and applications.
- Compare graphical user interfaces (GUIs) and command-line interfaces (CLIs).
- Navigate the Linux Filesystem Hierarchy Standard (FHS) and inspect logs using Bash commands (`ls`, `cd`, `cat`, `head`, `tail`, `find`, `grep`).
- Audit and modify file permissions and ownership with `ls -la`, `chmod`, and `chown` to enforce least privilege.
- Manage user accounts and understand responsible privilege elevation with `sudo`.
- Write SQL queries using `SELECT`, `FROM`, `WHERE`, `AND`, `OR`, `NOT`, `LIKE`, and `JOIN` to filter and correlate database records.

## Course modules

1. **Introduction to operating systems** – OS functions, hardware/software interaction, common operating systems, and GUI vs. CLI.
2. **The Linux operating system** – Linux architecture, Filesystem Hierarchy Standard, Linux distributions, Bash shell, and standard streams.
3. **Linux commands in the Bash shell** – File system navigation, searching and filtering logs, file permissions, user management, and `man` pages.
4. **Databases and SQL** – Relational database structure, SQL vs. Linux filtering, `WHERE` filter operators, and combining tables with SQL joins.

## Notes and activities

| File | Topic |
|---|---|
| [01 - Operating Systems and Interfaces](01-Operating-Systems-and-Interfaces.md) | OS functions, common operating systems, and GUI vs. CLI |
| [02 - Linux Architecture and Distributions](02-Linux-Architecture-and-Distributions.md) | Kernel, shell, FHS directories, distros, and I/O redirection |
| [03 - Linux File System and Log Filtering](03-Linux-File-System-and-Log-Filtering.md) | Navigation commands, `find`, `grep`, and built-in help |
| [04 - Linux Permissions and User Management](04-Linux-Permissions-and-User-Management.md) | Permission strings, `chmod`, `chown`, `sudo`, and user accounts |
| [05 - Linux File Permissions Portfolio Activity](05-Linux-File-Permissions-Portfolio-Activity.md) | Official Module 3 portfolio activity: auditing and fixing permissions in `/home/researcher2/projects` |
| [06 - Relational Databases and SQL Queries](06-Relational-Databases-and-SQL-Queries.md) | Relational tables, keys, `SELECT`/`WHERE`, and logical operators |
| [07 - SQL Joins and Log Investigation](07-SQL-Joins-and-Log-Investigation.md) | `INNER`, `LEFT`, `RIGHT`, and `FULL OUTER` joins with security examples |
| [08 - SQL Query Filters Portfolio Activity](08-SQL-Query-Filters-Portfolio-Activity.md) | Official Module 4 portfolio activity: filtering `log_in_attempts` and `employees` tables |
| [09 - Glossary](09-Glossary.md) | Key Linux and SQL terms from the course |

## Portfolio activities

This course includes two official Coursera portfolio activities:
1. **Use Linux commands to manage file permissions (Module 3):** Auditing `/home/researcher2/projects` with `ls -la` and updating permissions on `project_k.txt`, `project_m.txt`, `.project_x.txt`, and `drafts` using `chmod`.
2. **Apply filters to SQL queries (Module 4):** Writing six SQL `WHERE` queries with `AND`, `OR`, `NOT`, and `LIKE` across `log_in_attempts` and `employees`.

## Certificate

**Tools of the Trade: Linux and SQL**  
Provider: Google Career Certificates  
[View Course 4 Certificate](https://coursera.org/share/d36fb26ba4a29cf6b3b87c4d26ef7e92)
