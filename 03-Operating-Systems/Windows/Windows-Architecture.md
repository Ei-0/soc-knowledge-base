# 🪟 Windows Architecture

## 📌 Overview
The Windows operating system architecture is built on a **layered design** that separates user applications from critical system components.

From a **SOC and DFIR perspective**, understanding Windows architecture is essential because:
- Most enterprise environments rely on Windows
- The majority of malware targets Windows internals
- Logs, processes, and attacks map directly to architectural layers

---

## 🧱 High-Level Windows Architecture
Windows is divided into two main execution layers:

- **User Mode**
- **Kernel Mode**

<img width="663" height="850" alt="image" src="https://github.com/user-attachments/assets/9daf1478-8cfd-4e3b-951e-ad2df6cbb880" />

This separation enforces security, stability, and access control.

---

## 🧑‍💻 User Mode Components

### 🔹 Applications
- User-installed software
- Office applications
- Browsers
- Scripts and tools

🔍 **SOC View**:
- Initial malware execution often starts here
- Phishing payloads and droppers run as user applications

---

### 🔹 Subsystems
Subsystems provide environments for applications to run:
- Win32 subsystem (most common)
- Provides APIs for user applications

🔍 **SOC View**:
- Abused by malware using Windows APIs
- API misuse can indicate malicious activity

---

### 🔹 System Libraries (DLLs)
- Core Windows functionality
- Shared across applications

🔍 **SOC View**:
- DLL hijacking is a common attack technique
- Unsigned or suspicious DLL loads are red flags

---

## ⚙️ Kernel Mode Components

### 🔹 Windows Kernel
Responsible for:
- Process scheduling
- Memory management
- Hardware abstraction

🔍 **SOC View**:
- Kernel compromise = full system control
- Kernel exploits indicate advanced threats

---

### 🔹 Device Drivers
- Enable hardware communication
- Run with high privileges

🔍 **SOC View**:
- Vulnerable or unsigned drivers are frequently abused
- Driver abuse is used for privilege escalation

---

### 🔹 Hardware Abstraction Layer (HAL)
- Abstracts hardware differences
- Ensures OS portability

🔍 **SOC View**:
- Rarely attacked directly
- Involved in low-level system behavior

---

## 🔐 Windows Security Architecture

### 🔹 Security Reference Monitor (SRM)
- Enforces access control
- Validates permissions

🔍 **SOC View**:
- Privilege escalation attempts target SRM decisions

---

### 🔹 Local Security Authority (LSA)
- Manages authentication and credentials
- Stores sensitive secrets in memory

🔍 **SOC View**:
- Credential dumping attacks target LSA
- LSASS abuse is a critical alert

---

### 🔹 User Account Control (UAC)
- Limits administrative privileges
- Requires elevation for sensitive actions

🔍 **SOC View**:
- UAC bypass techniques are common
- Silent elevation attempts are suspicious

---

## 🔄 Windows Boot Process (Security Relevance)
1. Firmware initialization
2. Bootloader execution
3. Kernel loading
4. System services startup
5. User login

🔍 **SOC View**:
- Boot-level persistence is highly stealthy
- Early-stage malware is difficult to detect

---

## 🚨 Common Attack Paths in Windows
Attackers often:
- Execute malware in User Mode
- Abuse PowerShell or scripting engines
- Escalate privileges via vulnerable drivers
- Establish persistence using services or registry
- Disable security controls

Understanding architecture helps track these steps.

---

## 📊 What SOC Analysts Should Monitor
Key architectural indicators:
- User → Kernel privilege transitions
- Driver installations
- DLL load paths
- Security service tampering
- Unexpected system behavior

---

## 🧩 Mapping to MITRE ATT&CK
Windows architecture maps heavily to:
- Execution
- Privilege Escalation
- Persistence
- Defense Evasion
- Credential Access

Architecture knowledge accelerates ATT&CK mapping.

---

## 🧪 Real-World Example
1. User opens a phishing document
2. Macro spawns PowerShell (User Mode)
3. PowerShell drops a malicious DLL
4. DLL hijacking executes code
5. Vulnerable driver escalates privileges
6. Persistence is established

This chain spans multiple Windows layers.

---

## 🚀 What’s Next?
Continue with:

👉 **`Windows-Processes.md`**

Deep dive into how Windows processes work and how attackers abuse them.
