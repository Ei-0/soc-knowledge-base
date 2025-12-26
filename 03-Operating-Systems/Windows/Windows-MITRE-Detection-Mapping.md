# 🧠 Windows MITRE ATT&CK Detection Mapping (SOC-Focused)

## 📌 Overview
This document maps **Windows system behaviors** to **MITRE ATT&CK tactics and techniques**  
from a **SOC detection and investigation perspective**.

The goal is NOT to memorize MITRE —  
but to understand **how alerts, logs, and artifacts map to attacker behavior**.

---

## 🎯 How SOC Analysts Should Use MITRE
MITRE ATT&CK helps SOC analysts:
- Classify attacker behavior
- Correlate alerts into attack chains
- Identify detection gaps
- Communicate incidents clearly

MITRE answers **"WHAT the attacker did"**,  
logs answer **"HOW we know it happened"**.

---

## 🧱 Initial Access

### 🎯 Common Techniques
- Phishing
- Malicious attachments
- Drive-by downloads

### 🪟 Windows Detection Signals
- Office spawning PowerShell or CMD
- Execution from Downloads or Temp directories

### 📊 Logs & Artifacts
- Event ID **4688** (Process Creation)
- Email security logs
- File creation events

---

## ▶️ Execution

### 🎯 Common Techniques
- PowerShell
- Command-Line Interface
- LOLBins

### 🪟 Windows Detection Signals
- Encoded PowerShell commands
- LOLBins executing scripts or downloads

### 📊 Logs & Artifacts
- Event ID **4688**
- PowerShell Script Block Logs
- AMSI alerts

---

## ♻️ Persistence

### 🎯 Common Techniques
- Registry Run Keys
- Scheduled Tasks
- Windows Services
- Startup Folders

### 🪟 Windows Detection Signals
- New persistence shortly after execution
- Persistence pointing to user-writable paths

### 📊 Logs & Artifacts
- Event ID **4697** (Service Installed)
- Event ID **4698** (Scheduled Task Created)
- Registry modification events

---

## ⬆️ Privilege Escalation

### 🎯 Common Techniques
- UAC Bypass
- Vulnerable Drivers
- Token Manipulation

### 🪟 Windows Detection Signals
- Admin privileges without user interaction
- Driver loads from non-standard paths

### 📊 Logs & Artifacts
- Event ID **4672** (Special Privileges)
- Driver load telemetry
- EDR kernel alerts

---

## 🛡️ Defense Evasion

### 🎯 Common Techniques
- Obfuscation
- Log Clearing
- Security Tool Tampering
- Masquerading

### 🪟 Windows Detection Signals
- Event logs cleared
- Security services stopped
- Legitimate binaries used maliciously

### 📊 Logs & Artifacts
- Event ID **1102** (Audit Log Cleared)
- Service stop events
- EDR tamper alerts

---

## 🔐 Credential Access

### 🎯 Common Techniques
- LSASS Dumping
- Credential Manager Abuse
- Kerberos Attacks

### 🪟 Windows Detection Signals
- Access to LSASS memory
- Unusual credential access tools

### 📊 Logs & Artifacts
- EDR credential access alerts
- Sysmon process access events
- Memory dump artifacts

---

## 🌐 Lateral Movement

### 🎯 Common Techniques
- Pass-the-Hash
- Pass-the-Ticket
- Remote Services (SMB, RDP, WMI)

### 🪟 Windows Detection Signals
- Authentication across multiple hosts
- Admin logins from workstations

### 📊 Logs & Artifacts
- Event ID **4624** (Logon Type 3 / 10)
- Event ID **4768 / 4769**
- Remote service creation logs

---

## 📥 Collection

### 🎯 Common Techniques
- Automated data collection
- Credential harvesting
- System discovery

### 🪟 Windows Detection Signals
- Enumeration commands
- System info gathering

### 📊 Logs & Artifacts
- Process creation logs
- Command-line telemetry

---

## 📤 Exfiltration

### 🎯 Common Techniques
- Exfiltration over HTTP/S
- Cloud storage abuse
- Encrypted channels

### 🪟 Windows Detection Signals
- Large outbound transfers
- Network traffic from non-network tools

### 📊 Logs & Artifacts
- Proxy / Firewall logs
- EDR network telemetry

---

## 💥 Impact

### 🎯 Common Techniques
- Ransomware
- Data destruction
- Account lockout

### 🪟 Windows Detection Signals
- Mass file modifications
- Shadow copy deletion
- Backup tampering

### 📊 Logs & Artifacts
- File system events
- Service stop events
- Backup logs

---

## 🧩 Detection Thinking Example (SOC Mindset)

> ❌ Wrong:  
> “Alert: PowerShell execution”

> ✅ Correct:  
> “PowerShell execution → Persistence created → Credential access → Lateral movement  
> = Active intrusion (mapped to MITRE chain)”

SOC analysts detect **chains**, not single alerts.

---

## 🧠 Why This File Is Powerful
This file proves that you:
- Understand attacker behavior
- Understand Windows internals
- Think like a SOC analyst
- Can map alerts to threat models

This is **gold** for GitHub & interviews.

---

## 🚀 Optional Next (Elite Level)
- Detection Rules (Sigma-like)
- Threat Hunting Hypotheses
- Incident Response Playbooks
- Purple Team Mapping

---

## ✅ Final Note
MITRE is not a checklist.  
It’s a **language** SOC teams use to describe attacks.

Master the language → master detection.
