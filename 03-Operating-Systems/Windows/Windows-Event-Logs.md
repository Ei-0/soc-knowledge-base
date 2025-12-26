# 📜 Windows Event Logs

## 📌 Overview
**Windows Event Logs** are one of the most important data sources for SOC analysts.  
They record security, system, and application activities across the operating system.

From a **SOC and DFIR perspective**, event logs are essential for:
- Detecting attacks
- Investigating incidents
- Building timelines
- Supporting forensic analysis

If it’s not logged, it’s hard to prove.

---

## 🧱 What Are Windows Event Logs?
Windows logs events related to:
- User authentication
- Process execution
- Privilege changes
- System and service activity
- Application behavior

Logs are stored and viewed using **Event Viewer**.

<img width="1309" height="642" alt="image" src="https://github.com/user-attachments/assets/16c5fab8-f520-43c6-a8c9-8adacad2d463" />

---

## 🗂️ Main Windows Event Log Categories

## 📌 Important Windows Security Event IDs (SOC Reference)

| Event ID | Event Name / Description | Why It Matters (SOC View) |
|--------:|--------------------------|----------------------------|
| **4624** | Successful Logon | Detect legitimate vs suspicious logins (time, location, account). |
| **4625** | Failed Logon | Brute force attacks, password spraying, invalid access attempts. |
| **4634** | Logoff | Session tracking and timeline building. |
| **4648** | Logon with Explicit Credentials | Used by attackers for lateral movement (RunAs). |
| **4672** | Special Privileges Assigned | Indicates admin-level access (high-risk). |
| **4688** | Process Creation | One of the MOST important events for detection (parent/child, command line). |
| **4689** | Process Termination | Helps complete process execution timelines. |
| **4697** | Service Installed | Strong indicator of persistence or privilege escalation. |
| **4698** | Scheduled Task Created | Common persistence technique. |
| **4702** | Scheduled Task Updated | Indicates task tampering or persistence modification. |
| **4720** | User Account Created | Possible unauthorized account creation. |
| **4722** | User Account Enabled | Previously disabled account re-enabled (suspicious). |
| **4723** | Password Change Attempt | Credential abuse or account manipulation. |
| **4724** | Password Reset Attempt | Often used post-compromise. |
| **4728** | User Added to Privileged Group | Critical privilege escalation indicator. |
| **4732** | User Added to Local Group | Monitor for admin group additions. |
| **4740** | Account Locked Out | Can indicate brute force attacks. |
| **4768** | Kerberos TGT Requested | Used to detect Kerberos-based attacks. |
| **4769** | Kerberos Service Ticket | Useful for lateral movement detection. |
| **4776** | Credential Validation | NTLM authentication attempts. |
| **1102** | Audit Log Cleared | VERY high-risk (defense evasion). |
| **7045** | New Service Installed (System Log) | Common persistence mechanism. |

### SOC Analyst Tips
- Event **4688 + Command Line** = Gold mine for detections
- Event **4625 → 4624** sequence = Brute force success
- Event **1102** should ALWAYS trigger investigation
- New services and scheduled tasks are persistence favorites


### 🔹 Security Log
Records security-relevant events such as:
- Logons and logoffs
- Account creation and deletion
- Privilege escalation
- Policy changes

🔍 **SOC View**:
- Most critical log for threat detection
- Requires proper auditing to be enabled

---

### 🔹 System Log
Records events related to:
- System startup and shutdown
- Driver loading
- Service start and stop
- Hardware issues

🔍 **SOC View**:
- Useful for detecting persistence and boot-level issues
- Driver-related events are high value

---

### 🔹 Application Log
Records events from:
- Installed applications
- Third-party software
- Security tools

🔍 **SOC View**:
- Useful for detecting application abuse
- AV / EDR alerts often appear here

---

### 🔹 Other Logs
Additional important logs include:
- PowerShell logs
- Task Scheduler logs
- Windows Defender logs

These are critical for advanced detection.

---

## 🔐 Security Event Log (High-Value Events)
Common high-value event types:
- Successful and failed logins
- Account privilege changes
- Process creation
- Service installation

🔍 **SOC Tip**:
Context matters more than a single event.

---

## 🚨 Common Attacks Seen in Event Logs

### 🔹 Brute Force Attacks
Indicators include:
- Multiple failed login attempts
- Followed by a successful login

---

### 🔹 Privilege Escalation
Indicators include:
- User added to administrator groups
- Special privileges assigned

---

### 🔹 Persistence
Indicators include:
- New services created
- Scheduled tasks added
- Registry autorun changes

---

### 🔹 Defense Evasion
Indicators include:
- Log clearing events
- Security service stopped
- Auditing disabled

---

## 📊 What SOC Analysts Should Monitor
Key log-based signals:
- Authentication patterns
- Process execution events
- Service and task creation
- Changes to security policies
- Log tampering activity

Correlation across logs increases detection accuracy.

---

## 🧠 Log Correlation (Why It Matters)
Single events rarely tell the full story.

SOC analysts correlate:
- Authentication events
- Process creation
- Network connections
- Registry changes

This builds a **complete attack narrative**.

---

## 🧩 Mapping to MITRE ATT&CK
Windows Event Logs map to almost all ATT&CK tactics:
- Initial Access
- Execution
- Persistence
- Privilege Escalation
- Defense Evasion
- Credential Access

Strong logging = strong detection.

---

## 🧪 Real-World Example
1. Multiple failed login attempts detected
2. A successful login follows
3. New service creation event appears
4. Security logs are cleared shortly after

This sequence strongly indicates compromise.

---

## 🚀 What’s Next?
Continue with:

👉 **`Windows-Persistence-Mechanisms.md`**

This will consolidate all Windows persistence techniques in one place.
