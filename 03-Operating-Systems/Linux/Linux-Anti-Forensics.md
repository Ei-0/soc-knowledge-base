# 🕶️ Linux Anti-Forensics (SOC & DFIR)

## 📌 Overview
Anti-forensics refers to **techniques attackers use to hide their activity, destroy evidence,
or mislead investigations**.

From a SOC and DFIR perspective, anti-forensics is critical because:
- Skilled attackers attempt to erase or manipulate evidence
- Missing or altered data can indicate compromise
- Anti-forensics activity itself is often a **high-confidence IOC**

Attackers don’t just break in — they **clean up**.

---

## 🧱 Why Anti-Forensics Works on Linux
Attackers succeed because:
- Logs are often plaintext and writable by root
- Monitoring is weaker on servers than endpoints
- Administrators rarely audit historical integrity
- Many tools are built-in and trusted

Anti-forensics often requires **no malware**, only native commands.

---

## 🧨 Common Linux Anti-Forensics Techniques

## 1️⃣ Log Deletion & Truncation
Attackers delete or truncate logs to remove evidence.

Targets:
- `/var/log/auth.log`
- `/var/log/secure`
- `/var/log/syslog`
- `/var/log/messages`
- Application logs

Techniques:
- `rm -f`
- `truncate -s 0`
- Log rotation abuse

### SOC Indicators
- Missing logs or sudden size drops
- Gaps in authentication timelines
- Rotation occurring outside schedule

---

## 2️⃣ Shell History Manipulation
Attackers hide executed commands.

Techniques:
- Deleting `.bash_history`
- Clearing history (`history -c`)
- Disabling history logging
- Using non-interactive shells

### SOC Indicators
- Empty or missing history files
- Command execution with no history records
- Sudden history truncation

---

## 3️⃣ Timestamp Manipulation (Timestomping)
Attackers modify file timestamps to hide activity.

Techniques:
- `touch -t`
- Copying timestamps from legitimate files

### SOC Indicators
- Files with timestamps older than creation context
- Identical timestamps across unrelated files
- Timestamp inconsistencies vs logs

---

## 4️⃣ Process Masquerading
Malicious processes disguise as legitimate ones.

Examples:
- `kworker`
- `systemd-helper`
- `dbus-daemon`

Techniques:
- Renaming binaries
- Running from unusual paths

### SOC Indicators
- Legitimate process names running outside standard directories
- Parent process mismatch
- Unexpected command-line arguments

---

## 5️⃣ Fileless Execution
Attackers avoid writing files to disk.

Techniques:
- `curl | bash`
- In-memory execution via interpreters

### SOC Indicators
- Execution without corresponding file artifacts
- Network + shell execution correlation
- Activity visible only in process telemetry

---

## 6️⃣ Deleting or Disabling Security Tools
Attackers remove detection capability.

Targets:
- Auditd
- EDR agents
- Log forwarding services

Techniques:
- Stopping services
- Killing processes
- Removing binaries or configs

### SOC Indicators
- Sudden service stoppage
- Missing audit logs
- Agent tampering alerts

---

## 7️⃣ Clearing Evidence After Privilege Escalation
Attackers clean traces post-escalation.

Actions:
- Remove exploit files
- Clear sudo logs
- Delete cron entries after persistence is installed

### SOC Indicators
- Privilege escalation with no clear path
- Root access without corresponding sudo history
- Persistence present without creation logs

---

## 🚨 High-Risk Anti-Forensics Indicators
Treat the following as **critical**:
- Missing or truncated authentication logs
- Root activity without audit trails
- Evidence gaps during known intrusion windows
- Disabled logging or monitoring services
- Inconsistent timestamps across artifacts

Absence of evidence **can be evidence**.

---

## 📊 What SOC Analysts Should Monitor
High-value signals:
- Log file size changes
- Service stop/start events
- File metadata anomalies
- Gaps in timelines
- Differences between local and forwarded logs

Correlation across multiple data sources is essential.

---

## 🧩 MITRE ATT&CK Mapping
Linux anti-forensics maps to:
- Defense Evasion
- Impact
- Privilege Escalation
- Persistence

---

## 🧪 Real-World Anti-Forensics Example
1. Attacker gains SSH access
2. Escalates privileges via sudo
3. Deletes auth logs covering login window
4. Clears shell history
5. Leaves persistent backdoor via SSH key

The attack is revealed by **what is missing**, not what is present.

---

## 🧠 SOC Analyst Mindset
Always ask:
- Why is this data missing?
- Does the timeline make sense?
- Could logs have been altered?
- Is this absence consistent across systems?

On Linux, **anti-forensics often signals an experienced attacker**.

---

