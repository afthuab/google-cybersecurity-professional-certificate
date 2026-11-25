# Operating Systems and User Interfaces

## 1. What is an operating system?

An operating system (OS) is the core software that manages a computer's hardware and provides services so applications can run. Without an OS, each program would have to interact directly with physical components such as the CPU, memory, and storage drives.

The communication flow works in layers:

1. **User:** Initiates an action in an application or terminal.
2. **Application:** Sends a request to the operating system.
3. **Operating system (kernel):** Allocates CPU time, memory, and hardware access.
4. **Hardware:** Executes the instructions and returns output through the OS back to the user.

## 2. Main functions of an operating system

| Function | What it does | Security relevance |
|---|---|---|
| Resource allocation | Distributes CPU cycles, RAM, and disk space among running programs | Helps detect resource exhaustion caused by malware or cryptominers |
| Process management | Starts, schedules, pauses, and terminates running processes | Analysts inspect running processes to spot unexpected executables |
| Memory management | Tracks which processes occupy specific areas of RAM | Prevents unauthorized processes from reading sensitive memory |
| File system management | Organizes files and directories on storage media | Controls read, write, and execute permissions on system files |
| Device and driver management | Translates OS requests into hardware-specific instructions | Malicious or outdated drivers can introduce kernel-level risks |

## 3. Common operating systems

- **Linux:** Open-source OS widely used on servers, cloud instances, network appliances, and security analysis platforms.
- **Windows:** Dominant desktop and enterprise server OS; heavily managed through Active Directory and PowerShell.
- **macOS:** Unix-based desktop OS used on Apple hardware, commonly seen on developer and corporate laptops.
- **ChromeOS:** Lightweight OS built around the Chrome browser and cloud workflows.
- **Android and iOS:** Mobile operating systems with strict application sandboxing and permission models.

## 4. GUI vs. CLI

Users interact with an operating system through either a **Graphical User Interface (GUI)** or a **Command-Line Interface (CLI)**.

| Feature | Graphical User Interface (GUI) | Command-Line Interface (CLI) |
|---|---|---|
| Interaction | Windows, icons, menus, and mouse clicks | Text commands typed into a shell or terminal |
| Ease of discovery | Easier for beginners to browse visually | Requires knowing command names and syntax |
| Speed and repeatability | Slower for repetitive multi-step tasks | Fast; commands can be combined and saved as scripts |
| Remote server use | Uses more bandwidth and system resources | Lightweight; standard method for remote SSH administration |

## 5. Key point

While GUIs are helpful for visual tools such as Wireshark or SIEM dashboards, security analysts rely on the CLI to inspect servers, parse large text logs, and automate routine checks.

## References

- [NIST SP 800-123 – Guide to General Server Security](https://csrc.nist.gov/pubs/sp/800/123/final)
- [The Linux Foundation – Introduction to Linux](https://training.linuxfoundation.org/)
