# 🐧 Linux Architecture

## 📌 Overview
Linux is widely used across:
- Servers and data centers
- Cloud and containers
- Security appliances
- DevOps environments

For SOC and DFIR analysts, Linux architecture matters because:
- Attacker execution paths look different than Windows
- Logging and persistence mechanisms differ by distro/init system
- Privilege and file permission models are core to investigations

---

## 🧱 High-Level Linux Architecture
At a high level, Linux is split into:

- **User Space**
- **Kernel Space**

User space applications interact with the kernel through **system calls**.

---

## 🧑‍💻 User Space
User space includes:
- Shells (bash, zsh)
- System utilities (ls, ps, grep, curl)
- Services (nginx, sshd)
- Libraries (glibc)
- Package managers (apt, yum/dnf)

🔍 SOC View:
- Initial attacker activity often appears as shell commands + utilities
- “Living off the land” is extremely common on Linux (curl/wget/bash)

---

## ⚙️ Kernel Space
Kernel space controls:
- Process scheduling
- Memory management
- Networking stack
- Filesystems (VFS)
- Device drivers

🔍 SOC View:
- Kernel-level compromise is rarer but high impact (rootkits)
- Unusual kernel module activity can be a major indicator

---

## 🔄 System Calls (Why Analysts Care)
System calls are the boundary between user space and kernel space.

🔍 SOC View:
- Many behavioral detections (EDR/eBPF) are built on syscall activity:
  - process creation (fork/exec)
  - file access (open/read/write)
  - network connections (connect/send/recv)

---

## 🧩 Init Systems (Boot & Service Management)
Linux distros use init systems to start services at boot:
- **systemd** (most common today)
- SysVinit (legacy)
- Upstart (older Ubuntu)

🔍 SOC View:
- Persistence often abuses init systems (systemd units, init scripts)
- Understanding the init system tells you *where to look*

---

## 🧠 Linux Security Model (Quick View)
Linux security relies on:
- Users and groups
- Permissions (r/w/x)
- Ownership
- Capabilities (fine-grained privileges)
- Optional MAC controls (SELinux/AppArmor)

🔍 SOC View:
- Many compromises involve privilege escalation to root
- Misconfigurations are common entry points

---

## 🚀 What’s Next?
👉 **Linux-Logs.md** (syslog/journald/auth logs + SOC detection tips)
