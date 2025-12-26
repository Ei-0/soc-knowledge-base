# 🧩 Windows Services

## 📌 Overview
A **Windows service** is a long-running background process designed to perform system or application tasks without user interaction.

From a **SOC and DFIR perspective**, Windows services are a **high-value target** because:
- They often run with elevated privileges
- They start automatically with the system
- They provide reliable persistence for attackers

---

## 🧱 What Is a Windows Service?
Windows services:
- Run in the background
- Can start automatically at boot
- Often run as SYSTEM or service accounts
- Are managed by the Service Control Manager (SCM)

Services are critical to normal system operation.

---

## 🔄 Service Startup Types
Common startup types include:
- **Automatic** – Starts at system boot
- **Automatic (Delayed Start)** – Starts shortly after boot
- **Manual** – Starts when requested
- **Disabled** – Cannot be started

<img width="1266" height="636" alt="image" src="https://github.com/user-attachments/assets/de507ddf-8cbe-4b25-9052-22728da8ed64" />

🔍 **SOC View**:
- New or modified automatic services are high-risk
- Attackers prefer automatic startup for persistence

---

## ⚙️ Service Execution Context
Services run under specific accounts:
- LocalSystem
- LocalService
- NetworkService
- Custom user accounts

🔍 **SOC View**:
- Services running as SYSTEM have full control
- Unexpected service accounts are suspicious

---

## 🚨 Common Service Abuse Techniques

### 🔹 Malicious Service Creation
Attackers create new services to:
- Execute malware on startup
- Maintain persistence
- Run with high privileges

⚠️ Red Flags:
- Newly created services with random names
- Services pointing to executables in user-writable paths

---

### 🔹 Service Binary Replacement
Attackers replace or modify the service executable:
- Keeps service name legitimate
- Executes malicious code instead

---

### 🔹 Service Configuration Tampering
Attackers modify:
- Startup type
- Binary path
- Service permissions

This allows persistence without creating new services.

---

<img width="804" height="552" alt="image" src="https://github.com/user-attachments/assets/e71c5d79-9d23-47e7-ba7d-dd0b6097a7af" />

## 🧠 Windows Services and Persistence
Services are commonly used for:
- Long-term persistence
- Privilege escalation
- Defense evasion

They are reliable and stealthy if not monitored.

---

## 📊 What SOC Analysts Should Monitor
Critical service-related telemetry:
- Service creation events
- Service start/stop events
- Changes to service configuration
- Service binary path changes
- Service account changes

Windows Event Logs and EDR are key sources.

---

## 🧩 Mapping to MITRE ATT&CK
Windows service abuse maps to:
- Persistence
- Privilege Escalation
- Defense Evasion

Monitoring services significantly improves detection coverage.

---

## 🧪 Real-World Example
1. Attacker gains initial access
2. Drops a malicious executable in `C:\ProgramData`
3. Creates a new Windows service pointing to the file
4. Sets startup type to Automatic
5. Malware executes on every reboot

This is a **classic persistence technique**.

---

## 🚀 What’s Next?
Continue with:

👉 **`Windows-Registry.md`**

This will explain how attackers abuse the Windows Registry for persistence and stealth.
