# ♻️ Linux Persistence Mechanisms (SOC & DFIR)

## 📌 Overview
Persistence techniques allow attackers to **maintain access** to a Linux system after initial compromise.

From a SOC and DFIR perspective, persistence is critical because:
- It enables attackers to survive reboots
- It allows long-term access for lateral movement or data exfiltration
- It often blends into legitimate system behavior

Detecting persistence is often the key to fully removing an attacker.

---

## 🧱 Why Persistence Is Effective on Linux
Attackers rely on:
- Legitimate startup mechanisms
- Trusted configuration files
- Minimal security monitoring on servers
- Administrator assumptions of “normal behavior”

Persistence usually does **not** require exploits.

---

## 🔑 Common Linux Persistence Mechanisms

## 1️⃣ Cron Jobs
Scheduled execution via cron.

Common locations:
- `/etc/crontab`
- `/etc/cron.d/`
- `/var/spool/cron/`
- User crontabs

### SOC Indicators
- Cron jobs executing shells or download commands
- Recently created cron entries after initial access

---

## 2️⃣ systemd Services
Modern Linux persistence relies heavily on `systemd`.

Persistence methods:
- New malicious `.service` files
- Modified legitimate services
- User-level systemd services

Common paths:
- `/etc/systemd/system/`
- `/lib/systemd/system/`
- `~/.config/systemd/user/`

### SOC Indicators
- Services running scripts or shells
- Services executing from non-standard paths
- New services shortly after compromise

---

## 3️⃣ SSH Authorized Keys
Attackers add their SSH public keys for passwordless access.

Location:
- `~/.ssh/authorized_keys`

### SOC Indicators
- New keys added to privileged users
- Same key reused across multiple systems

---

## 4️⃣ Shell Startup Files
Shell profiles execute commands automatically.

Files:
- `~/.bashrc`
- `~/.bash_profile`
- `~/.profile`
- `/etc/profile`

### SOC Indicators
- Obfuscated commands
- Network or execution logic inside profiles

---

## 5️⃣ Init Scripts (Legacy)
Older systems may use:
- `/etc/init.d/`
- `/etc/rc.local`

### SOC Indicators
- Rare in modern systems
- Presence often indicates persistence

---

## 6️⃣ Environment Variable Abuse
Persistence via:
- `LD_PRELOAD`
- `LD_LIBRARY_PATH`

### SOC Indicators
- Unexpected environment variables
- Execution hijacking behavior

---

## 🚨 High-Risk Persistence Patterns
- Persistence pointing to `/tmp` or home directories
- Use of `curl`, `wget`, or `bash`
- Obfuscated commands
- Multiple persistence layers

---

## 📊 What SOC Analysts Should Monitor
- Cron modifications
- systemd unit changes
- SSH key changes
- Shell startup file edits
- Environment variable usage

---

## 🧩 MITRE ATT&CK Mapping
- Persistence
- Defense Evasion
- Privilege Escalation
