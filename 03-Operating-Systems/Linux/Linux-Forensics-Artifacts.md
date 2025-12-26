# 🕵️ Linux Forensics Artifacts (SOC & DFIR)

## 📌 Overview
Forensic artifacts are traces left by system and attacker activity.

In Linux investigations, artifacts allow analysts to:
- Reconstruct timelines
- Identify attacker actions
- Validate alerts
- Support incident response

Artifacts are the **evidence**.

---

## 🗂️ Key Categories of Linux Artifacts

## 1️⃣ Authentication Artifacts
Show access activity:
- SSH logins
- sudo usage
- User creation

Sources:
- `/var/log/auth.log`
- `/var/log/secure`

---

## 2️⃣ Process Artifacts
Reveal execution:
- Command lines
- Parent-child relationships
- Execution paths

Sources:
- `/proc`
- auditd
- EDR telemetry

---

## 3️⃣ Persistence Artifacts
Show long-term access:
- Cron jobs
- systemd services
- SSH keys
- Shell profiles

Sources:
- `/etc/cron*`
- systemd unit files
- `~/.ssh/authorized_keys`

---

## 4️⃣ File System Artifacts
Show file activity:
- Created or modified binaries
- Script drops
- Timestamp changes

Sources:
- File metadata
- Backup logs
- File integrity tools

---

## 5️⃣ Privilege Escalation Artifacts
Show elevation paths:
- sudo logs
- SUID binaries
- Capability changes

Sources:
- sudo logs
- auditd
- File permissions

---

## 6️⃣ Network Artifacts
Show communication:
- Outbound connections
- SSH pivoting
- Data exfiltration

Sources:
- Netflow
- Firewall logs
- EDR network telemetry

---

## ⏱️ Timeline Reconstruction
SOC and DFIR teams correlate:
- Authentication events
- Process execution
- Persistence creation
- Privilege escalation
- Lateral movement

Timelines expose the full attack chain.

---

## 🚨 Anti-Forensics Indicators
Attackers may:
- Delete logs
- Clear history
- Modify timestamps
- Disable monitoring

Missing artifacts are often evidence.

---

## 🧠 SOC Analyst Mindset
Always ask:
- What evidence proves this happened?
- Can the timeline be reconstructed?
- Is persistence still active?
- Did the attacker try to hide?

---

## 🧩 MITRE ATT&CK Mapping
Linux forensic artifacts support:
- Execution
- Persistence
- Privilege Escalation
- Credential Access
- Lateral Movement
- Defense Evasion
