# 🧪 Linux Detection Rules (SOC & DFIR – Pseudo Rules)

## 📌 Overview
This file contains **practical Linux detection logic** written in a **pseudo-rule format**  
(similar to Sigma, EDR, or SIEM logic).

Purpose:
- Translate Linux attack behavior into detections
- Show SOC detection thinking (not tool-specific syntax)
- Provide a foundation for SIEM / EDR / auditd rules

These are **behavior-based detections**, not signatures.

---

## 🧱 How to Read These Rules
Each rule contains:
- **Detection Goal** – what we want to catch
- **Data Sources** – logs or telemetry required
- **Logic** – simplified detection condition
- **Why It Matters** – attacker behavior explained
- **MITRE Mapping**

---

## 🔐 Rule 1: SSH Brute Force Followed by Success

### Detection Goal
Detect SSH brute force attacks that result in successful access.

### Data Sources
- Authentication logs (`auth.log`, `secure`)

### Detection Logic
- Multiple failed SSH logins from same IP
- Followed by a successful login
- Within a short time window

### Why It Matters
This pattern indicates **credential guessing or password spraying**
and is a common Linux initial access method.

### MITRE Mapping
- Initial Access

---

## 🔓 Rule 2: SSH Login Followed by Immediate sudo

### Detection Goal
Detect potential privilege escalation after SSH access.

### Data Sources
- Authentication logs
- sudo logs

### Detection Logic
- SSH login success
- sudo command executed by same user
- Within minutes of login

### Why It Matters
Attackers often escalate privileges immediately after gaining access.

### MITRE Mapping
- Privilege Escalation

---

## ♻️ Rule 3: Cron Persistence Creation After Login

### Detection Goal
Detect cron jobs created shortly after authentication.

### Data Sources
- File integrity monitoring
- Cron logs
- Authentication logs

### Detection Logic
- New or modified cron entry
- Created shortly after SSH login
- Command executes shell or interpreter

### Why It Matters
Cron is one of the most abused Linux persistence mechanisms.

### MITRE Mapping
- Persistence
- Execution

---

## ⚙️ Rule 4: systemd Service Created from User Path

### Detection Goal
Detect malicious systemd persistence.

### Data Sources
- File system monitoring
- systemd logs

### Detection Logic
- New `.service` file created
- Executable path points to `/tmp`, `/var/tmp`, or user home

### Why It Matters
Legitimate services rarely execute from writable directories.

### MITRE Mapping
- Persistence
- Defense Evasion

---

## 🧨 Rule 5: Fileless Execution via curl | bash

### Detection Goal
Detect fileless malware execution.

### Data Sources
- Process execution logs
- Command-line telemetry

### Detection Logic
- Process contains `curl` or `wget`
- Output piped to `bash` or `sh`

### Why It Matters
This is one of the most common Linux malware execution techniques.

### MITRE Mapping
- Execution
- Defense Evasion

---

## 🧠 Rule 6: Shell Spawned by systemd or cron

### Detection Goal
Detect suspicious process ancestry.

### Data Sources
- Process telemetry

### Detection Logic
- Parent process is `systemd` or `cron`
- Child process is interactive shell

### Why It Matters
systemd and cron should rarely spawn interactive shells.

### MITRE Mapping
- Persistence
- Execution

---

## 🔑 Rule 7: SSH Key Added to Privileged Account

### Detection Goal
Detect SSH key-based persistence.

### Data Sources
- File integrity monitoring
- User home directory changes

### Detection Logic
- `authorized_keys` modified
- User is root or sudo-enabled
- Modification outside maintenance window

### Why It Matters
SSH keys provide silent, long-term access.

### MITRE Mapping
- Persistence
- Credential Access

---

## 🌐 Rule 8: Outbound Network Connection from Shell

### Detection Goal
Detect reverse shells or C2 traffic.

### Data Sources
- Network telemetry
- Process telemetry

### Detection Logic
- Process is shell or interpreter
- Establishes outbound connection
- Destination is unusual or external

### Why It Matters
Shells rarely initiate network connections legitimately.

### MITRE Mapping
- Command and Control
- Exfiltration

---

## 🛡️ Rule 9: Log Deletion or Truncation

### Detection Goal
Detect anti-forensics behavior.

### Data Sources
- File integrity monitoring
- System logs

### Detection Logic
- Auth or system log size drops suddenly
- File deleted or truncated

### Why It Matters
Attackers often remove logs to hide activity.

### MITRE Mapping
- Defense Evasion
- Impact

---

## 🚨 Rule 10: UID Transition to Root Without Clear Path

### Detection Goal
Detect suspicious privilege escalation.

### Data Sources
- Process telemetry
- Authentication logs

### Detection Logic
- Process runs as UID 0
- Parent process runs as non-root
- No corresponding sudo or auth event

### Why It Matters
Indicates misconfiguration abuse or kernel exploitation.

### MITRE Mapping
- Privilege Escalation

---

## 🧠 SOC Detection Philosophy
Good Linux detections focus on:
- **Sequence**, not single events
- **Context**, not binaries
- **Behavior**, not tools

One alert rarely equals one incident.

---

## 🚀 How to Use This File
- Convert logic into SIEM queries
- Translate into Sigma rules
- Build EDR detections
- Use as threat-hunting hypotheses

This file proves you can **think like a detection engineer**.

---


