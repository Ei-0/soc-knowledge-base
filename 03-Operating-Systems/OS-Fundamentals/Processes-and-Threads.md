# ⚙️ Processes and Threads

## 📌 Overview
A **process** is an instance of a running program, while a **thread** is the smallest unit of execution within a process.

From a security and SOC perspective, **processes and threads are the core of execution visibility**.  
Every attack, script, or malware sample must execute as a process and often abuses threads.

---

## 🧱 What Is a Process?
A process includes:
- Executable code
- Memory space
- Open files
- Network connections
- Security context (user privileges)

Each process runs in isolation from others.

---

### 🔍 Security Perspective (Processes)
SOC analysts analyze processes to:
- Identify malicious executables
- Detect abnormal execution behavior
- Trace attack chains

⚠️ Red Flags:
- Unknown processes running from user-writable directories
- System processes running from incorrect paths
- Unexpected parent-child process relationships

---

## 🧵 What Is a Thread?
A thread:
- Exists inside a process
- Shares the process memory space
- Executes tasks concurrently

A single process can contain **multiple threads** running simultaneously.

---

### 🔍 Security Perspective (Threads)
Attackers abuse threads to:
- Inject malicious code into legitimate processes
- Hide execution within trusted applications
- Evade basic process-based detection

⚠️ Red Flags:
- Suspicious thread injection
- Abnormal thread start addresses
- High thread activity in benign processes

---

## 🔄 Process Lifecycle
Typical process stages:
1. Creation
2. Execution
3. Termination

SOC analysts should focus on:
- How the process was created
- Who created it
- What it spawned

---

## 👨‍👩‍👦 Parent-Child Process Relationships
Processes often create other processes.

🔍 Why This Matters:
- Attack chains rely heavily on abnormal spawning
- Many detections are based on parent-child logic

⚠️ Suspicious Examples:
- Office applications spawning PowerShell
- Browsers launching command-line tools
- Scripts spawning system utilities

---

## 🧠 Process Injection (Common Attack Technique)
Process injection allows attackers to:
- Execute code inside trusted processes
- Bypass application allowlists
- Evade detection

Common injection methods:
- DLL injection
- Process hollowing
- Thread hijacking

---

## 📊 What SOC Analysts Should Monitor
Key process-related data points:
- Process name and path
- Parent process
- Command-line arguments
- User context
- Hash values
- Network activity

These signals are critical for EDR and SIEM detection.

---

## 🧩 Mapping to MITRE ATT&CK
Processes and threads are directly linked to:
- Execution
- Defense Evasion
- Privilege Escalation

Many ATT&CK techniques rely on abusing process behavior.

---

## 🧪 Real-World Example
1. User opens a malicious email attachment
2. Document spawns PowerShell
3. PowerShell injects code into explorer.exe
4. Malicious activity runs under a trusted process

This technique is widely used by modern malware.

---

## 🚀 What’s Next?
Continue with:

👉 **`Memory-Management.md`**

This will explain how attackers abuse memory and how SOC analysts detect it.
