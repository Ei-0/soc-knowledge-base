# 🧬 Windows Registry

## 📌 Overview
The **Windows Registry** is a hierarchical database that stores configuration settings for:
- The operating system
- Applications
- Users
- Hardware

From a **SOC and DFIR perspective**, the Registry is a **gold mine of artifacts** and one of the **most abused persistence mechanisms**.

---

## 🧱 What Is the Windows Registry?
The Registry stores:
- System configuration
- Startup settings
- Installed software information
- User preferences
- Security-related data

It is loaded into memory at boot and accessed constantly by Windows.

---

<img width="688" height="413" alt="image" src="https://github.com/user-attachments/assets/e923243f-83e9-485e-a219-24eb0842e248" />

## 🗂️ Registry Structure (Hives)
The Registry is divided into **hives**, each serving a specific purpose:

- **HKEY_LOCAL_MACHINE (HKLM)**  
  System-wide settings

- **HKEY_CURRENT_USER (HKCU)**  
  Current user configuration

- **HKEY_USERS (HKU)**  
  All user profiles

- **HKEY_CLASSES_ROOT (HKCR)**  
  File associations and COM objects

<img width="573" height="395" alt="image" src="https://github.com/user-attachments/assets/949e09d9-a7c5-40ac-979b-ae24cd5c4a3a" />

🔍 **SOC View**:
- HKLM affects the entire system
- HKCU is commonly abused for user-level persistence

---

## 🔄 How the Registry Is Used at Startup
During boot and login, Windows reads Registry keys to:
- Start services
- Launch startup applications
- Configure drivers
- Load security settings

Attackers abuse this behavior to ensure malware runs automatically.

---

## 🚨 Common Registry Abuse Techniques

### 🔹 Autorun Keys (Persistence)
Attackers add entries to keys such as:
- `Run`
- `RunOnce`
- `RunServices`

These keys cause executables to launch at user login or system startup.

---

### 🔹 Image File Execution Options (IFEO)
IFEO can be abused to:
- Redirect execution of legitimate programs
- Launch malicious binaries instead

🔍 **SOC View**:
- Rarely used legitimately
- High-fidelity detection point

---

### 🔹 AppInit_DLLs
Allows DLLs to be loaded into processes:
- Used for legitimate extensions
- Abused for stealthy injection

---

### 🔹 Service-Related Keys
Services store configuration in the Registry:
- Binary path
- Startup type
- Permissions

Tampering here can hide malicious services.

---

## 🧠 Registry and Stealth
Attackers favor the Registry because:
- It blends with normal system activity
- Changes persist across reboots
- Many security tools trust Registry data

---

## 📊 What SOC Analysts Should Monitor
High-value Registry monitoring areas:
- Startup and autorun keys
- IFEO keys
- Service configuration keys
- Changes in security-related Registry paths
- Unexpected Registry modifications by user processes

Registry telemetry is essential for persistence detection.

---

## 🧩 Mapping to MITRE ATT&CK
Registry abuse maps to:
- Persistence
- Privilege Escalation
- Defense Evasion

Many ATT&CK techniques rely on Registry modifications.

---

## 🧪 Real-World Example
1. Malware executes under a user account
2. Adds itself to a Registry Run key
3. User logs out or reboots
4. Malware launches automatically at login
5. Persistence is achieved without creating new files

---

## 🚀 What’s Next?
Continue with:

👉 **`Windows-Event-Logs.md`**

This will cover how SOC analysts detect attacks using Windows logging.
