# 🔐 Kernel Mode vs User Mode

## 📌 Overview
Modern operating systems separate execution into **two main privilege levels**:

- **User Mode**
- **Kernel Mode**

This separation is one of the **most critical security boundaries** in any operating system.  
Breaking or bypassing this boundary often leads to **full system compromise**.

---

## 🧱 User Mode

### 🔹 What Is User Mode?
User Mode is where:
- Applications run
- User-level processes execute
- Most software operates with limited privileges

Programs in User Mode **cannot directly access**:
- Hardware
- Kernel memory
- Critical system resources

They must request access through the operating system.

---

### 🔍 Security Perspective (User Mode)
From a SOC perspective:
- Most malware starts execution in User Mode
- Phishing payloads, scripts, and droppers run here
- Suspicious user-level processes are often the **first indicator**

⚠️ Red Flags:
- Unknown executables running under user accounts
- Office apps spawning PowerShell or CMD
- Browsers launching system utilities

---

## 🧱 Kernel Mode

### 🔹 What Is Kernel Mode?
Kernel Mode is the **most privileged execution level** where:
- The OS kernel runs
- Device drivers operate
- Hardware interaction occurs
- Memory management is enforced

Code running in Kernel Mode has **unrestricted access** to the system.

---

### 🔍 Security Perspective (Kernel Mode)
From a SOC perspective:
- Kernel compromise = total system control
- Rootkits often aim to run in Kernel Mode
- Kernel-level malware is harder to detect

⚠️ Red Flags:
- Unsigned or suspicious drivers
- Kernel crashes linked to unknown modules
- Disabled security features (EDR, AV)

---

## 🔄 How User Mode Communicates with Kernel Mode
User Mode applications interact with Kernel Mode via:
- System calls
- APIs
- Interrupts

This design ensures:
- Stability
- Security isolation
- Controlled access to sensitive resources

Attackers often try to **abuse or exploit** these interfaces.

---

## 🚨 Kernel Exploitation (Why It Matters)
Attackers target Kernel Mode to:
- Bypass security controls
- Disable EDR/AV
- Hide processes and files
- Maintain stealthy persistence

Common techniques include:
- Exploiting vulnerable drivers
- Privilege escalation exploits
- Loading malicious kernel modules

---

## 🧠 SOC Detection Opportunities

### 🔹 Indicators of Kernel Abuse
SOC analysts should monitor for:
- Unexpected driver installation
- Driver loads from unusual paths
- Kernel-related event logs
- Sudden loss of security telemetry

---

### 🔹 Questions SOC Analysts Should Ask
- How did this process gain elevated privileges?
- Was a vulnerable driver involved?
- Did a user-mode process escalate unexpectedly?
- Are kernel protections disabled?

---

## 🧩 Mapping to MITRE ATT&CK
Kernel vs User Mode is directly related to:
- Privilege Escalation
- Defense Evasion
- Persistence

Many high-impact techniques require **crossing this boundary**.

---

## 🧪 Real-World Example
1. User opens a malicious document
2. Macro spawns PowerShell (User Mode)
3. Exploit abuses a vulnerable driver
4. Attacker gains Kernel Mode execution
5. Security tools are disabled

This is a **classic escalation chain**.

---

## 🚀 What’s Next?
Continue with:

👉 **`Processes-and-Threads.md`**

This will help you understand how attackers hide, inject, and abuse processes.
