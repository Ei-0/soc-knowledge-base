# 🧠 Linux MITRE ATT&CK Detection Mapping (SOC-Focused)

## 📌 Overview
This document maps **Linux attacker behaviors** to **MITRE ATT&CK tactics and techniques**  
from a **SOC detection and investigation perspective**.

The goal is not memorization, but to:
- Understand attacker intent
- Correlate alerts into attack chains
- Identify detection gaps
- Communicate incidents clearly

MITRE explains **WHAT the attacker did**.  
Logs and telemetry explain **HOW we know**.

---

## 🎯 How SOC Analysts Use MITRE on Linux
SOC analysts use MITRE to:
- Classify suspicious behavior
- Build incident timelines
- Prioritize alerts
- Explain attacks to stakeholders

MITRE is most powerful when combined with **process, auth, and persistence telemetry**.

---

## 🧱 Initial Access

### 🎯 Common Techniques
- SSH brute force
- Exploiting public-facing services
- Compromised credentials

### 🪟 Linux Detection Signals
- Repeated SSH authentication failures
- Successful login after many failures
- Login from unusual IPs or geolocations

### 📊 Logs & Artifacts
- `/var/log/auth.log` or `/var/log/secure`
- SSH daemon logs
- Cloud access logs (if applicable)

---

## ▶️ Execution

### 🎯 Common Techniques
- Shell execution
- Script execution (bash, python, perl)
- Living-off-the-land binaries

### 🪟 Linux Detection Signals
- Shells spawned by SSH, cron, or services
- Command chaining and obfuscation
- Download-and-execute patterns

### 📊 Logs & Artifacts
- Process command-line telemetry
- auditd execve logs
- EDR process events

---

## ♻️ Persistence

### 🎯 Common Techniques
- Cron jobs
- systemd services
- SSH authorized_keys
- Shell startup files

### 🪟 Linux Detection Signals
- New persistence shortly after access
- Persistence pointing to user-writable paths
- Multiple persistence layers on one host

### 📊 Logs & Artifacts
- Cron file changes
- systemd unit modifications
- SSH key file changes

---

## ⬆️ Privilege Escalation

### 🎯 Common Techniques
- sudo misconfiguration
- SUID binary abuse
- Capabilities abuse
- Kernel exploits

### 🪟 Linux Detection Signals
- UID transition to 0 (root)
- Root shells spawned by user processes
- Execution of uncommon SUID binaries

### 📊 Logs & Artifacts
- sudo logs
- auditd UID/GID change events
- File permission changes

---

## 🛡️ Defense Evasion

### 🎯 Common Techniques
- Log deletion or truncation
- Disabling security tools
- Obfuscation
- Masquerading processes

### 🪟 Linux Detection Signals
- Missing or cleared logs
- Security agents stopped
- Legitimate binaries used maliciously

### 📊 Logs & Artifacts
- Log rotation anomalies
- Service stop events
- EDR tamper alerts

---

## 🔐 Credential Access

### 🎯 Common Techniques
- Harvesting SSH keys
- Reading config files
- Memory scraping (rare)

### 🪟 Linux Detection Signals
- Access to `.ssh` directories
- Credential files accessed by shells
- Rapid reuse of credentials

### 📊 Logs & Artifacts
- File access audit logs
- SSH authentication logs
- Process access telemetry

---

## 🌐 Lateral Movement

### 🎯 Common Techniques
- SSH credential reuse
- SSH agent forwarding
- Shared storage abuse
- Cloud API pivoting

### 🪟 Linux Detection Signals
- One host authenticating to many others
- Identical SSH keys across systems
- Privileged account spreading

### 📊 Logs & Artifacts
- SSH auth logs across hosts
- Source/destination correlation
- Cloud audit logs

---

## 📥 Collection

### 🎯 Common Techniques
- System discovery
- File enumeration
- Credential harvesting

### 🪟 Linux Detection Signals
- Execution of discovery commands
- Access to sensitive directories
- Enumeration scripts

### 📊 Logs & Artifacts
- Process execution logs
- Command history artifacts

---

## 📤 Exfiltration

### 🎯 Common Techniques
- Exfiltration over HTTPS
- SCP / rsync abuse
- Cloud storage abuse

### 🪟 Linux Detection Signals
- Large outbound transfers
- Network activity from non-network tools
- Transfers outside normal schedules

### 📊 Logs & Artifacts
- Network flow logs
- Proxy logs
- EDR network telemetry

---

## 💥 Impact

### 🎯 Common Techniques
- Data destruction
- Resource hijacking (crypto-mining)
- Service disruption

### 🪟 Linux Detection Signals
- High CPU usage
- Mass file deletion or encryption
- Service outages

### 📊 Logs & Artifacts
- System performance metrics
- File system events
- Service crash logs

---

## 🧠 Detection Thinking Example (SOC Mindset)

❌ Single-alert thinking:
“Suspicious SSH login”

✅ Detection-chain thinking:
“SSH brute force → successful login → cron persistence → sudo escalation → lateral SSH movement”

SOC detects **chains**, not isolated alerts.

---

## 🧩 Why This File Matters
This mapping demonstrates:
- Understanding of Linux internals
- Ability to connect logs to attacker behavior
- Strong SOC analytical thinking
- Practical MITRE usage


---

