# 🐧 Linux Basics (SOC & DFIR Foundation)

## 📌 Overview
Linux Basics provides the **foundational knowledge** required before diving into
Linux security, detection, and forensics.

For SOC analysts, Linux basics are critical because:
- Most servers, cloud workloads, and containers run Linux
- Attacks rely heavily on native commands and filesystem knowledge
- Logs, permissions, and processes behave very differently from Windows

Without strong Linux fundamentals, investigations become guesswork.

---

## 🧱 What Is Linux?
Linux is:
- An open-source operating system kernel
- The core of many operating systems (Ubuntu, Debian, RHEL, CentOS, Amazon Linux)

A typical Linux system consists of:
- Kernel
- User space utilities
- Shell
- Services (daemons)
- File system hierarchy

---

## 🖥️ Linux Distributions (Distros)
Linux comes in different distributions, each with:
- Different package managers
- Slightly different configurations
- Similar core behavior

Common enterprise distros:
- Ubuntu / Debian
- Red Hat Enterprise Linux (RHEL)
- CentOS / Rocky / Alma
- Amazon Linux

SOC relevance:
- Logs and paths may differ slightly
- Core attack techniques remain the same

---

## 💻 The Linux Shell
The shell is the **primary user interface** on Linux.

Common shells:
- `bash` (most common)
- `sh`
- `zsh`

SOC relevance:
- Most attacker activity is visible as shell commands
- Shell history and execution context are valuable artifacts

---

## 📂 Linux File System Hierarchy
Linux uses a single-root filesystem: `/`

Key directories:
- `/bin` – Essential binaries
- `/sbin` – System binaries (admin)
- `/etc` – Configuration files
- `/home` – User home directories
- `/var` – Logs and variable data
- `/tmp` – Temporary files
- `/usr` – User binaries and libraries

SOC relevance:
- Malware often hides in `/tmp`, `/var/tmp`, or user home directories
- Changes in `/etc` often indicate persistence or misconfiguration

---

## 👤 Users and Groups
Linux uses:
- Users (UID)
- Groups (GID)

Special user:
- `root` (UID 0) → full system control

SOC relevance:
- Unexpected users or UID 0 access is high risk
- Group membership (sudo/admin) is critical for privilege escalation

---

## 🔐 File Permissions (Basic View)
Linux permissions control access using:
- Read (r)
- Write (w)
- Execute (x)

Applied to:
- Owner
- Group
- Others

SOC relevance:
- World-writable files are dangerous
- Executable files in writable directories are suspicious

---

## ⚙️ Processes (Basic View)
Everything running on Linux is a process.

Each process has:
- PID
- Parent PID
- User context
- Command line

SOC relevance:
- Parent–child relationships reveal attack chains
- Unexpected process execution is a primary detection signal

---

## 🧾 Linux Logging (Basic View)
Most logs live under:
- `/var/log/`

Important logs:
- Authentication logs
- System logs
- Application logs

SOC relevance:
- Logs are essential for detection and timelines
- Missing logs may indicate tampering

---

## 🌐 Networking Basics
Linux systems frequently act as:
- Servers
- Proxies
- Application backends

SOC relevance:
- Outbound connections from shells are suspicious
- SSH is the most common remote access method

---

## 🚨 Common Beginner Mistakes (Security Impact)
- Running services as root
- Reusing SSH keys
- Weak sudo configurations
- Ignoring logs
- Leaving default credentials

Attackers exploit fundamentals first.

---

## 🧠 SOC Analyst Mindset
When analyzing Linux systems, always ask:
- What is the role of this system?
- Which users should exist?
- Which services should run?
- What commands make sense here?

Abnormal behavior is easier to detect when fundamentals are clear.

---
