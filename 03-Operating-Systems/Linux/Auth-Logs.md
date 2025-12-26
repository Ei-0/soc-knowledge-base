# 🔐 Linux Authentication Logs (SOC & DFIR)

## 📌 Overview
Authentication logs on Linux record **who accessed the system, how, and from where**.

For SOC and DFIR analysts, auth logs are among the **most critical data sources** because:
- Almost every intrusion starts with authentication
- Brute-force, credential abuse, and lateral movement all appear here
- Authentication events anchor investigation timelines

If you understand auth logs, you understand **entry points**.

---

## 🧱 Where Linux Authentication Logs Live
The exact path depends on the distribution:

### Debian / Ubuntu
- `/var/log/auth.log`

### RHEL / CentOS / Rocky / Alma
- `/var/log/secure`

These logs are usually written by:
- `sshd`
- `sudo`
- PAM (Pluggable Authentication Modules)

---

## 🔑 Key Authentication Events

### SSH Successful Login
Indicates a user successfully authenticated.

SOC relevance:
- First foothold in most attacks
- Must be validated against source IP, user, and time

High-risk indicators:
- Success after multiple failures
- Login from unusual country or IP
- Login outside normal hours

---

### SSH Failed Login
Indicates authentication failure.

SOC relevance:
- Brute force and password spraying detection
- Baseline for normal failure rates

High-risk indicators:
- High-volume failures
- Multiple users targeted from same IP
- Repeated failures followed by success

---

### sudo Usage
Records privilege elevation attempts.

SOC relevance:
- Often precedes full compromise
- Key indicator of privilege escalation

High-risk indicators:
- sudo used by unexpected users
- sudo usage shortly after SSH login
- sudo spawning shells or editors

---

### User and Group Changes
Authentication logs often record:
- New user creation
- Group membership changes
- Password changes

SOC relevance:
- Persistence and privilege escalation
- Unauthorized account creation

---

## 🌐 Source Information
Auth logs record:
- Source IP address
- Authentication method
- Target user

SOC relevance:
- Enables detection of lateral movement
- Correlation across hosts is critical

---

## 🚨 Common Attack Patterns in Auth Logs

### Brute Force Attack
Pattern:
- Many failed logins
- Followed by a successful login

SOC action:
- Investigate source IP
- Check for persistence creation

---

### Credential Stuffing
Pattern:
- Same password tried across multiple users

SOC action:
- Identify compromised credentials
- Enforce password resets

---

### Lateral Movement via SSH
Pattern:
- One host authenticating to many others
- Same user appearing across servers

SOC action:
- Trace credential reuse
- Check SSH key propagation

---

## 🧪 Example Auth Log Timeline
1. Repeated SSH failures from external IP
2. Successful login as valid user
3. sudo executed shortly after
4. SSH login to internal server from compromised host

Auth logs reveal the **entire intrusion flow**.

---

## 🛡️ Log Tampering & Evasion
Attackers may attempt to:
- Delete auth logs
- Truncate log files
- Disable logging
- Rotate logs aggressively

SOC relevance:
- Missing logs are suspicious
- Gaps in authentication records indicate tampering

---

## 📊 What SOC Analysts Should Monitor
High-value indicators:
- SSH failures and successes
- sudo executions
- User/group changes
- Source IP patterns
- Time-based anomalies

Auth logs are often the **starting point of investigations**.

---

## 🧩 MITRE ATT&CK Mapping
Linux authentication activity maps to:
- Initial Access
- Credential Access
- Lateral Movement
- Persistence

---

## 🧠 SOC Analyst Mindset
Always ask:
- Is this login expected for this user?
- Is the source normal for this host?
- Did authentication lead to execution or persistence?
- Is this part of a broader pattern?

Authentication tells you **how the door was opened**.

---

