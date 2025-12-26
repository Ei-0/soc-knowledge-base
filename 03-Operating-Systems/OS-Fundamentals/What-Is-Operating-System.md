# 🖥️ What Is an Operating System?

## 📌 Definition
An **Operating System (OS)** is system software that manages computer hardware and software resources and provides common services for applications.

From a **SOC and security perspective**, the operating system is the **central control layer** where:
- Users authenticate
- Processes execute
- Memory is allocated
- Files are accessed
- Logs are generated

Almost every cyber attack interacts with the operating system at some level.

---

## 🎯 Why Operating Systems Matter in Cybersecurity
Security analysts must understand operating systems because:

- Attacks abuse OS components (processes, services, memory)
- Indicators of Compromise (IOCs) appear in OS logs
- Persistence mechanisms rely on OS startup behavior
- Privilege escalation targets OS permissions

Without OS knowledge, threat detection becomes guesswork.

---

## 🧱 Core Responsibilities of an Operating System

### 1️⃣ Process Management
- Creates, schedules, and terminates processes
- Controls execution order and resource usage
- Enables multitasking

🔍 **Security View**:
- Malicious processes often masquerade as legitimate ones
- Abnormal parent-child process relationships are red flags

---

### 2️⃣ Memory Management
- Allocates and deallocates RAM
- Isolates process memory
- Manages virtual memory

🔍 **Security View**:
- Malware may inject code into other processes
- Memory abuse can indicate exploitation

---

### 3️⃣ File System Management
- Organizes data into files and directories
- Controls file permissions and access
- Tracks file metadata

🔍 **Security View**:
- Unauthorized file creation or modification is suspicious
- Timestamp manipulation may indicate anti-forensics

---

### 4️⃣ User and Permission Management
- Manages users, groups, and roles
- Enforces access control

🔍 **Security View**:
- Unexpected admin accounts are critical alerts
- Privilege escalation attempts target this layer

---

### 5️⃣ Device and I/O Management
- Controls hardware devices (disk, network, USB)
- Manages drivers

🔍 **Security View**:
- Rogue drivers may indicate rootkits
- USB usage is a common exfiltration vector

---

## 🖥️ Common Types of Operating Systems

### 🔹 Desktop Operating Systems
- Windows
- macOS
- Linux (Desktop distributions)

Used by end users and commonly targeted by phishing and malware.

---

### 🔹 Server Operating Systems
- Windows Server
- Linux Server distributions

Primary targets for ransomware and lateral movement.

---

### 🔹 Embedded & Specialized OS
- Routers, IoT devices, firewalls

Often overlooked but high-risk due to weak security controls.

---

## 🧭 OS Perspective for SOC Analysts
SOC analysts should always ask:
- What process executed?
- Under which user account?
- What files were accessed?
- What logs were generated?
- Does this behavior align with the system role?

Answering these questions builds the foundation of effective investigations.

---

## 🧠 Mapping OS Knowledge to MITRE ATT&CK
Most MITRE ATT&CK techniques map directly to OS behavior:
- Execution
- Persistence
- Privilege Escalation
- Defense Evasion

Understanding the OS helps quickly map alerts to ATT&CK techniques.

---

## 🚀 What’s Next?
Continue with:

👉 **`Kernel-vs-User-Mode.md`**

This will explain how attackers cross privilege boundaries and how SOC analysts detect it.
