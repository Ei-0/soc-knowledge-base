# 🧠 Memory Management

## 📌 Overview
Memory management is one of the most critical responsibilities of an operating system.  
It controls how memory is allocated, used, and protected.

From a **security and SOC perspective**, memory is a **prime target for attackers** because:
- Code can execute without touching disk
- Memory-based attacks evade traditional detection
- Sensitive data may exist only in RAM

---

## 🧱 What Is Memory Management?
Memory management involves:
- Allocating memory to processes
- Isolating memory between processes
- Managing virtual memory
- Protecting kernel and user memory spaces

Each process receives its own virtual address space.

---

## 🔄 Virtual Memory
Virtual memory allows:
- Processes to use more memory than physically available
- Isolation between processes
- Efficient memory utilization

The OS maps **virtual addresses** to **physical memory**.

---

### 🔍 Security Perspective (Virtual Memory)
Attackers exploit virtual memory to:
- Inject code into other processes
- Perform buffer overflow attacks
- Execute shellcode in memory

SOC analysts should watch for:
- Unusual memory allocations
- Execution from non-standard memory regions

---

## 🚨 Memory-Based Attacks

### 🔹 Process Injection
Malware injects code into a legitimate process’s memory to:
- Hide execution
- Bypass security controls

---

### 🔹 Fileless Malware
Fileless malware:
- Executes entirely in memory
- Leaves little or no disk artifacts
- Relies on scripts or trusted binaries

---

### 🔹 Credential Dumping
Sensitive credentials often reside in memory:
- LSASS (Windows)
- Authentication caches

Attackers dump memory to extract passwords or hashes.

---

## 🧠 Memory Protections
Modern operating systems implement:
- DEP (Data Execution Prevention)
- ASLR (Address Space Layout Randomization)
- Kernel memory isolation

Attackers attempt to bypass or disable these protections.

---

## 📊 SOC Detection Opportunities
SOC analysts should monitor:
- Suspicious memory access attempts
- Abnormal process memory behavior
- Credential dumping indicators
- Sudden crashes related to memory misuse

---

## 🧩 Mapping to MITRE ATT&CK
Memory abuse is commonly associated with:
- Execution
- Credential Access
- Defense Evasion

Understanding memory behavior helps analysts detect advanced threats.

---

## 🧪 Real-World Example
1. Malware executes PowerShell
2. PowerShell downloads payload into memory
3. Payload injects into a trusted process
4. No file is written to disk

This is a common **fileless attack** pattern.

---

## 🚀 What’s Next?
Continue with:

👉 **`File-Systems-Overview.md`**

This will explain how attackers manipulate files and metadata.
