# 🪵 Linux Logs (SOC & DFIR)

## 📌 Overview
Linux logging varies by distro and configuration, but the key idea is consistent:
logs are usually stored under **/var/log**, and modern systems often use **systemd-journald**.

For SOC analysts, Linux logs help answer:
- Who logged in?
- What commands ran?
- What services started/stopped?
- What failed/authenticated?
- Was persistence created?

---

## 🧱 Two Common Logging Worlds

### 🔹 1) syslog (rsyslog/syslog-ng)
Classic logging pipeline:
- Services write to syslog
- syslog forwards to files in `/var/log/*`

### 🔹 2) journald (systemd-journald)
Modern pipeline:
- Logs stored in journal database
- Viewed via `journalctl`
- Can forward to syslog/files if configured

---

## 📂 High-Value Log Files (Common Paths)
> Paths can differ slightly across distros.

### 🔹 Authentication Logs (Most Important)
- Debian/Ubuntu: `/var/log/auth.log`
- RHEL/CentOS: `/var/log/secure`

SOC uses:
- SSH logins
- sudo usage
- user additions
- authentication failures

---

### 🔹 System & Service Logs
- `/var/log/syslog` (Debian/Ubuntu)
- `/var/log/messages` (RHEL-based)
- `journalctl -u <service>` (systemd units)

SOC uses:
- service start/stop events
- daemon errors
- persistence-related service changes

---

### 🔹 Web / Application Logs (If Applicable)
- nginx: `/var/log/nginx/access.log`, `/var/log/nginx/error.log`
- apache: `/var/log/apache2/access.log`, `/var/log/apache2/error.log`

SOC uses:
- suspicious user agents
- scanning patterns
- exploitation attempts (e.g., webshell drops)

---

## 🔐 Linux Authentication Events (What to Look For)

### ✅ SSH Success / Failure
- Repeated failures → brute force or password spraying
- Success after many failures → likely compromise

### ✅ Sudo Activity
- Unexpected sudo usage
- sudo from unusual users or at unusual times

### ✅ User/Group Changes
- New users created
- users added to sudo/admin groups

---

## 🚨 Common Log Tampering & Evasion
Attackers may:
- delete or truncate log files
- disable forwarding
- clear journal (less common but possible)
- rotate logs aggressively to remove evidence

SOC tip:
- Missing logs can be evidence itself.

---

## 🧠 SOC Detection Ideas (Linux)
High-signal detections:
- SSH login from unusual IP + immediate sudo
- New user creation + SSH key added shortly after
- Cron/systemd unit created after suspicious shell activity
- “curl/wget | bash” patterns
- Base64/obfuscated bash commands

---

## 🧩 Mapping to MITRE ATT&CK
Linux logs commonly support:
- Initial Access (SSH brute force)
- Execution (shell commands)
- Persistence (cron/systemd)
- Privilege Escalation (sudo, su)
- Defense Evasion (log deletion)
- Lateral Movement (SSH pivoting)

---

## 🚀 What’s Next?
👉 **Linux-Processes.md** (ps, procfs, parent/child, malicious patterns)
