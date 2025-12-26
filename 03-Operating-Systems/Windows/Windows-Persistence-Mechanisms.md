# ♻️ Windows Persistence Mechanisms

## 📌 Overview
**Persistence** refers to techniques used by attackers to maintain access to a system after initial compromise.

From a **SOC and DFIR perspective**, persistence mechanisms are critical because:
- They allow attackers to survive reboots
- They enable long-term access
- They are often reused across malware families

Detecting persistence = breaking the attacker’s foothold.

---

## 🧱 Why Windows Persistence Is Common
Attackers favor Windows persistence because:
- Windows provides many legitimate startup mechanisms
- Persistence blends with normal system behavior
- Many techniques require no exploits once access is gained

Understanding these mechanisms is essential for effective detection.

---

## 🔑 Common Windows Persistence Mechanisms

### 🔹 1. Registry Autorun Keys
Registry keys that execute programs at startup or login.

Common locations:
- User-level autoruns
- System-wide autoruns

🔍 **SOC View**:
- Executables in user-writable paths are suspicious
- Random value names are red flags

---

### 🔹 2. Windows Services
Attackers create or modify services to:
- Run malware with high privileges
- Start automatically on boot

🔍 **SOC View**:
- New services with unusual names
- Service binaries outside system directories

---

### 🔹 3. Scheduled Tasks
Scheduled Tasks allow execution:
- At boot
- At logon
- On a schedule
- On specific triggers

🔍 **SOC View**:
- Tasks running scripts or LOLBins
- Tasks created by non-admin users

---

### 🔹 4. Startup Folders
Programs placed in startup folders run automatically.

🔍 **SOC View**:
- Rarely used by modern software
- Frequently abused by malware

---

### 🔹 5. DLL Search Order Hijacking
Attackers place malicious DLLs where applications load them first.

🔍 **SOC View**:
- Unexpected DLL loads
- DLLs in application directories

---

### 🔹 6. WMI Event Subscriptions
WMI can trigger execution based on events.

🔍 **SOC View**:
- Extremely stealthy
- Rarely used legitimately
- High-confidence persistence when detected

---

### 🔹 7. Boot-Level Persistence
Persistence that executes during early boot stages.

🔍 **SOC View**:
- Difficult to detect
- Often indicates advanced threat actors

---

## 🚨 High-Risk Persistence Indicators
SOC analysts should treat the following as high risk:
- Persistence pointing to user-writable directories
- Use of scripting engines (PowerShell, cmd)
- Obfuscated commands
- Newly created persistence shortly after compromise

---

## 📊 What SOC Analysts Should Monitor
Key telemetry sources:
- Registry changes
- Service creation/modification events
- Scheduled task creation
- Startup folder file creation
- WMI activity
- Boot configuration changes

Correlation is key.

---

## 🧩 Mapping to MITRE ATT&CK
Windows persistence maps mainly to:
- **Persistence**
- **Privilege Escalation**
- **Defense Evasion**

Many techniques overlap across these tactics.

---

## 🧪 Real-World Attack Chain Example
1. Initial access via phishing
2. Malware execution in user context
3. Registry autorun key added
4. Scheduled task created as backup
5. Service installed for SYSTEM-level access

Attackers often use **multiple persistence layers**.

---

## 🧠 SOC Analyst Mindset
Always ask:
- How does this survive a reboot?
- Is this persistence legitimate?
- When was it created?
- What user created it?
- What does it execute?

Persistence answers often reveal the attacker.

---

## 🚀 What’s Next?
Continue with:

👉 **`Windows-Common-Attacks.md`**

This will tie Windows internals to real attack techniques and detection logic.
