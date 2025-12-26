# 📁 Linux File System (SOC & DFIR)

## 📌 Overview
The Linux file system defines **how data is stored, accessed, and managed** on a system.

From a SOC and DFIR perspective, the file system is critical because:
- Attackers must interact with files at some stage
- Persistence often relies on file placement
- Forensic investigations depend on file metadata
- Misplaced or modified files often reveal compromise

Understanding the Linux file system allows analysts to **spot what does not belong**.

---

## 🧱 Linux File System Structure
Linux uses a **single-root hierarchy** starting at `/`.

Everything on the system is accessible through this tree.

---

## 📂 Key Directories and SOC Relevance

### `/bin`
Essential user binaries (e.g., `ls`, `cp`, `bash`).

SOC relevance:
- Rarely modified
- Malicious files here are extremely suspicious

---

### `/sbin`
System binaries, mainly for administration.

SOC relevance:
- Executables should be trusted
- Any change may indicate root-level compromise

---

### `/etc`
Configuration files for the system and services.

SOC relevance:
- High-value target for persistence
- Changes may indicate service hijacking or backdoors
- Includes sudo rules, SSH config, cron configs

---

### `/home`
User home directories.

SOC relevance:
- Common location for dropped tools
- SSH keys stored here
- User-level persistence often lives here

---

### `/var`
Variable data such as logs, caches, and spools.

Important subdirectories:
- `/var/log` – system and application logs
- `/var/tmp` – temporary files

SOC relevance:
- Log tampering often targets `/var/log`
- Malware may hide in writable subdirectories

---

### `/tmp`
Temporary file storage.

SOC relevance:
- World-writable
- Common malware staging area
- Files here are often short-lived

---

### `/usr`
User applications and libraries.

SOC relevance:
- Normally stable
- Unexpected binaries or scripts are suspicious

---

### `/opt`
Optional or third-party software.

SOC relevance:
- Attackers may hide tools here
- Often overlooked during audits

---

### `/dev`
Device files.

SOC relevance:
- Rarely abused directly
- Abuse may indicate advanced activity

---

### `/proc`
Virtual filesystem exposing process and system info.

SOC relevance:
- Critical for live response
- Reveals command lines, open files, memory usage
- Used to detect fileless malware

---

### `/boot`
Bootloader and kernel files.

SOC relevance:
- Changes indicate very high-impact compromise
- Boot-level persistence may exist here

---

## ⏱️ File Metadata (Why It Matters)
Linux tracks metadata such as:
- Modification time (mtime)
- Access time (atime)
- Change time (ctime)
- Ownership and permissions

SOC relevance:
- Timestamp inconsistencies may indicate tampering
- Metadata helps build attack timelines

---

## 🚨 Common File System Abuse Techniques

### 🔹 Hidden Files
Attackers hide files using:
- Dot-prefixed names (e.g., `.backdoor`)
- Deep directory nesting

---

### 🔹 Masquerading
Malware disguises itself as legitimate files:
- Similar names
- Legitimate-looking paths

---

### 🔹 Persistence via Files
Persistence often relies on:
- Scripts referenced by cron
- systemd service files
- Modified shell profiles

---

### 🔹 Anti-Forensics
Attackers may:
- Delete logs
- Modify timestamps
- Remove files after execution

Missing files can still leave metadata or log traces.

---

## 📊 What SOC Analysts Should Monitor
High-value indicators:
- New executables in writable directories
- Changes in `/etc`
- Unexpected file permission changes
- Files executed from `/tmp` or `/var/tmp`
- Modifications shortly after suspicious logins

---

## 🧩 MITRE ATT&CK Mapping
Linux file system abuse maps to:
- Execution
- Persistence
- Defense Evasion
- Privilege Escalation

---

## 🧪 Real-World Example
1. Attacker gains SSH access
2. Drops script in `/tmp`
3. Executes script
4. Moves persistence file to `/etc/cron.d`
5. Deletes original script

The file system reveals each stage.

---

## 🧠 SOC Analyst Mindset
Always ask:
- Does this file belong here?
- Who created or modified it?
- When did this change occur?
- Is this path appropriate for execution?

On Linux, **location often tells the story**.

---

