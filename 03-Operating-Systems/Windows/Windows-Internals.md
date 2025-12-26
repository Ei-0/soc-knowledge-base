# 🧠 Windows Internals

## 📌 Overview
Windows Internals refers to the **low-level components and mechanisms** that make the Windows operating system function.

For **SOC and DFIR analysts**, understanding internals helps:
- Explain *why* attacks work
- Detect stealthy techniques
- Investigate advanced threats
- Analyze EDR and kernel-level alerts

---

## 🧱 Core Windows Internal Components

### 🔹 Windows Kernel
Responsible for:
- Process scheduling
- Memory management
- Hardware interaction

🔍 SOC View:
- Kernel exploitation = full compromise
- Kernel crashes or anomalies may indicate rootkits

---

### 🔹 System Processes (Critical)
Key processes include:
- `System`
- `smss.exe`
- `csrss.exe`
- `wininit.exe`
- `services.exe`
- `lsass.exe`

🔍 SOC View:
- These should run from **System32**
- Any deviation is HIGH RISK

---

### 🔹 Memory Management Internals
Windows uses:
- Virtual memory
- Paging
- Kernel vs User memory isolation

🔍 SOC View:
- Memory-only malware bypasses disk detection
- Credential dumping targets memory

---

### 🔹 Object Manager
Manages:
- Processes
- Threads
- Files
- Registry objects

🔍 SOC View:
- Object access anomalies can indicate abuse

---

## 🚨 Why Windows Internals Matter for Detection
Many advanced attacks rely on:
- Kernel drivers
- Token manipulation
- Handle abuse
- Memory injection

Without internals knowledge, these attacks look invisible.

---

## 🧩 Mapping to MITRE ATT&CK
Windows internals are involved in:
- Privilege Escalation
- Defense Evasion
- Credential Access
- Persistence

---
