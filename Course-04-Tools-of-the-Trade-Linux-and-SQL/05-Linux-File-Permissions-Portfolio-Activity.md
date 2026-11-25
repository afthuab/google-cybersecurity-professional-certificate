# Portfolio Activity: Use Linux Commands to Manage File Permissions

## 1. Purpose

This portfolio activity documents how to inspect file and directory permissions in Bash (`ls -la`) and update misconfigured permissions with `chmod` so access matches organizational authorization rules.

This write-up is an independently documented summary based on the Course 4 Module 3 lab scenario (`Manage authorization` / `Use Linux commands to manage file permissions`). Outputs below are recreated to illustrate the commands and verification steps.

## 2. Scenario

Working as a security analyst for a research organization, I needed to audit permissions inside `/home/researcher2/projects` for the user `researcher2` (a member of `research_team`). The review required checking standard files, hidden files, and subdirectories against the following rules:

- Users in the `other` category must not have write permission on any file in `projects`.
- `project_m.txt` must only be accessible by its owner (`researcher2`).
- Hidden archived file `.project_x.txt` must be read-only for `researcher2` and `research_team` (no write permissions for anyone).
- Subdirectory `drafts` must only be accessible by `researcher2` (group execute access removed).

## 3. Initial permission inspection

Navigating to the `projects` directory and running `ls -la` reveals both standard items and the hidden file `.project_x.txt`:

```bash
cd /home/researcher2/projects
ls -la
```

```text
total 24
drwxr-xr-x 3 researcher2 research_team 4096 May  2 16:55 .
drwxr-xr-x 5 researcher2 research_team 4096 May  2 16:40 ..
drwx--x--- 2 researcher2 research_team 4096 May  2 16:55 drafts
-rw-rw-rw- 1 researcher2 research_team   46 May  2 16:55 project_k.txt
-rw-r----- 1 researcher2 research_team   46 May  2 16:55 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 May  2 16:55 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 May  2 16:55 project_t.txt
-rw--w---- 1 researcher2 research_team   46 May  2 16:55 .project_x.txt
```

## 4. Permission findings and required changes

| Item | Initial permissions | Issue identified | Command applied |
|---|---|---|---|
| `project_k.txt` | `-rw-rw-rw-` | `other` has write (`w`) permission, allowing any local user to modify the file | `chmod o-w project_k.txt` |
| `project_m.txt` | `-rw-r-----` | `research_team` group has read (`r`) access to a restricted owner-only file | `chmod g-r project_m.txt` |
| `.project_x.txt` | `-rw--w----` | Hidden archived file still allows write (`w`) for user and group, and lacks group read (`r`) | `chmod u-w,g-w,g+r .project_x.txt` |
| `drafts/` | `drwx--x---` | `research_team` group has execute (`x`) permission to enter the restricted directory | `chmod g-x drafts` |
| `project_r.txt` | `-rw-rw-r--` | Compliant (read/write for owner and group, read-only for other) | No change needed |
| `project_t.txt` | `-rw-rw-r--` | Compliant (read/write for owner and group, read-only for other) | No change needed |

## 5. Commands executed

```bash
# 1. Remove write permission for other users on project_k.txt
chmod o-w project_k.txt

# 2. Remove read permission for the group on project_m.txt so only researcher2 has access
chmod g-r project_m.txt

# 3. Make archived hidden file .project_x.txt read-only for owner and group
chmod u-w,g-w,g+r .project_x.txt

# 4. Remove group execute permission on the drafts directory
chmod g-x drafts
```

## 6. Verification

Running `ls -la` after applying the changes confirms all files and directories match the intended authorization settings:

```bash
ls -la
```

```text
total 24
drwxr-xr-x 3 researcher2 research_team 4096 May  2 17:10 .
drwxr-xr-x 5 researcher2 research_team 4096 May  2 16:40 ..
drwx------ 2 researcher2 research_team 4096 May  2 16:55 drafts
-rw-rw-r-- 1 researcher2 research_team   46 May  2 16:55 project_k.txt
-rw------- 1 researcher2 research_team   46 May  2 16:55 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 May  2 16:55 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 May  2 16:55 project_t.txt
-r--r----- 1 researcher2 research_team   46 May  2 16:55 .project_x.txt
```

## 7. Key learning

Using `ls -la` rather than `ls -l` ensures hidden dot-files (`.project_x.txt`) are included in permission reviews, and symbolic `chmod` arguments (`u`, `g`, `o` with `+` and `-`) allow precise adjustments without disturbing unrelated permission bits.

## References

- [GNU Coreutils – File permissions](https://www.gnu.org/software/coreutils/manual/html_node/File-permissions.html)
- [CIS Linux Benchmark Concepts – File System Permissions](https://www.cisecurity.org/cis-benchmarks)
