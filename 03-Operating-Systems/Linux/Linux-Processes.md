# Linux Processes 🐧

> Status: **ACTIVE / REVISED**
> Scope: SOC • Blue Team • DFIR • Threat Hunting  
> Platform: Linux (Userland + Kernel interaction)

This document provides a **clean, corrected, and unified explanation of Linux processes** with a strong **security and detection mindset**.

---

## 1️⃣ Definition: What Is a Linux Process?

A **process** is a running instance of a program in memory.

A process is NOT:
- The binary file on disk
- A service definition
- A cron job

A process IS:
- Code + memory + execution context

Each process has:
- **PID** (Process ID)
- **PPID** (Parent Process ID)
- **UID / GID**
- **Executable path**
- **Command-line arguments**
- **Environment variables**
- **State**

---

## 2️⃣ Process Creation Model (fork / exec)

Linux follows a **two-step execution model**:

```text
# Linux Process Analysis – SOC & DFIR Notes

## Parent Process
```
Parent Process
   |
   ├─ fork()  → Child created (copy)
   |
   └─ exec()  → New program loaded
```

### fork()
- Creates a child process  
- Child initially mirrors the parent  
- New PID assigned  

### exec()
- Replaces memory with a new program  
- PID stays the same  
- Most attacks start here  

📌 **Security note:**  
Attackers abuse trusted parents (sshd, systemd, cron) to execute payloads via exec.

---

## 3️⃣ Parent–Child Relationship
Linux process hierarchy matters.

### Example:
```
systemd (1)
 └── sshd (422)
     └── bash (931)
         └── python (2011)
```

### Why SOC cares
- Parent process gives **execution context**  
- Child process gives **intent**

### 🚩 Red Flags:
- Web server spawning a shell  
- System service spawning network tools  
- User shell spawning kernel-like processes  

---

## 4️⃣ Process States
| State | Meaning |
|-------|---------|
| R | Running / Runnable |
| S | Sleeping (interruptible) |
| D | Uninterruptible sleep (I/O wait) |
| T | Stopped / Traced |
| Z | Zombie |

### Detection Notes
- Persistent Zombies → broken or malicious parent logic  
- Long D state → possible I/O abuse or kernel hook issues  

---

## 5️⃣ Process Visibility & Inspection

### Core Commands
```bash
ps aux
ps -ef
ps -eo pid,ppid,user,cmd
```

### Tree View
```bash
pstree -p
```

### Runtime View
```bash
top
htop
```

---

## 6️⃣ /proc Filesystem (Critical for DFIR)
Every process has a directory:

```
/proc/<PID>/
```

### Important files:
- **cmdline** → exact execution  
- **exe** → binary path  
- **environ** → environment variables  
- **fd/** → open files & sockets  
- **status** → state, UID, capabilities  

### 🚩 Indicator:
```
/proc/PID/exe -> (deleted)
```
→ Fileless or self-deleting malware

---

## 7️⃣ Privilege & Execution Context
Processes execute with:
- UID / GID  
- Linux capabilities  
- SELinux / AppArmor context  

### Check ownership:
```bash
ps -o pid,user,group,cmd -p <PID>
```

### 🚩 Red Flags:
- Root process from user session  
- SUID binary spawning shell  
- Privilege jump without sudo logs  

---

## 8️⃣ Process Masquerading
Common attacker techniques:
- Legitimate names  
- System-looking paths  
- Argument obfuscation  

### Examples:
```
kworker (running in user space)
systemd-update
sshd --fake
```

### Detection:
- Verify binary location  
- Validate parent  
- Inspect arguments  

---

## 9️⃣ In-Memory / Fileless Execution
### Indicators:
- Executable deleted but process alive  
- Execution from /dev/shm, /tmp  
- Anonymous memory mappings  

### Common in:
- Post-exploitation frameworks  
- Kernel exploits  
- C2 loaders  

---

## 🔟 Process-Based Persistence
Persistence often re-spawns processes via:
- cron  
- systemd services  
- ~/.bashrc, ~/.profile  
- Init scripts  

### Detection:
- Process returns after kill  
- Process appears after reboot  

---

## 1️⃣1️⃣ Logs Related to Process Activity
Relevant logs:
- /var/log/auth.log  
- /var/log/syslog  
- /var/log/messages  
- /var/log/audit/audit.log  

### Auditd execution records:
```
type=EXECVE
type=SYSCALL
```

### Correlation fields:
- UID  
- Command  
- Parent PID  
- Timestamp  

---

## 1️⃣2️⃣ SOC Detection Use Cases

### Behavioral
- Shell from non-interactive service  
- Network tools executed by system users  
- Unusual parent-child chains  

### Threat Hunting
- (deleted) executables  
- Root processes from /tmp  
- Long-running reverse shells  

---

## 1️⃣3️⃣ MITRE ATT&CK Mapping
| Technique | Description |
|----------|-------------|
| T1059 | Command and Scripting Interpreter |
| T1055 | Process Injection |
| T1036 | Masquerading |
| T1543 | Create or Modify System Process |
| T1078 | Valid Accounts |

---

## 1️⃣4️⃣ Key Takeaways
- Processes tell the execution story  
- Parent matters as much as the child  


/proc is your strongest forensic source

Detection without process context is blind
