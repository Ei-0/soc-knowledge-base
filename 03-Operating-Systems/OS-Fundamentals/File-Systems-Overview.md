# 📁 File Systems Overview

## 📌 Overview
A **file system** defines how data is stored, organized, and accessed on a storage device.

From a **SOC and DFIR perspective**, file systems are critical because:
- Malware must store files at some point
- Attackers manipulate file metadata to evade detection
- Forensic investigations rely heavily on file system artifacts

Understanding file systems helps analysts detect **tampering, persistence, and anti-forensics**.

---

## 🧱 What Is a File System?
A file system manages:
- File creation, deletion, and modification
- Directory structures
- File permissions and ownership
- Metadata (timestamps, attributes)

Each operating system uses specific file system types.

---

## 🖥️ Common File Systems by OS

### 🔹 Windows
- NTFS (primary)
- FAT32 / exFAT (removable media)

Key characteristics:
- Rich metadata
- Access Control Lists (ACLs)
- Alternate Data Streams (ADS)

---

### 🔹 Linux
- ext4 (most common)
- xfs, btrfs

Key characteristics:
- Strong permission model
- Inodes for metadata
- Extensive logging support

---

### 🔹 macOS
- APFS (modern)
- HFS+ (legacy)

Key characteristics:
- Snapshots
- Strong encryption support
- Metadata-rich structure

---

## ⏱️ File Metadata (Why It Matters)
File systems store metadata such as:
- Creation time
- Modification time
- Access time
- File size
- Ownership

🔍 **Security Perspective**:
- Timestamp inconsistencies may indicate tampering
- Malware may alter timestamps to blend in
- Metadata helps build attack timelines

---

## 🚨 Common File System Abuses

### 🔹 Hidden Files
Attackers hide files by:
- Using hidden attributes
- Placing files in obscure directories

---

### 🔹 Masquerading
Malware disguises itself as legitimate files:
- Similar names
- Legitimate extensions
- System-like icons

---

### 🔹 Living Off the Land (LOLBins)
Attackers abuse legitimate binaries:
- Write minimal files
- Use trusted system paths

---

### 🔹 Anti-Forensics
Attackers attempt to:
- Delete logs
- Modify timestamps
- Securely wipe files

---

## 📂 Important Directories for SOC Analysts

### 🔹 Windows
- System directories
- User profile paths
- Temporary directories
- Startup folders

---

### 🔹 Linux
- /etc
- /var/log
- /tmp
- /home

---

### 🔹 macOS
- /Applications
- /Library
- /Users
- LaunchAgents / LaunchDaemons paths

---

## 📊 What SOC Analysts Should Monitor
Key indicators include:
- File creation in sensitive directories
- Executables in user-writable paths
- Unexpected changes to system files
- Suspicious file extensions or names

File-based telemetry is essential for SIEM and EDR detection.

---

## 🧩 Mapping to MITRE ATT&CK
File system abuse maps to:
- Persistence
- Defense Evasion
- Execution

Understanding file behavior helps quickly classify attacker techniques.

---

## 🧪 Real-World Example
1. Malware drops an executable into a user temp directory
2. File timestamps are modified to look legitimate
3. Startup mechanism references the file
4. Persistence is achieved with minimal visibility

---

## 🚀 What’s Next?
OS Fundamentals is now complete ✅

Next section:

👉 **`Windows/Windows-Architecture.md`**

This is where we move into **deep, OS-specific security analysis**.
