# ♻️ Linux Persistence Mechanisms (SOC & DFIR)

## 📌 Overview
Persistence refers to techniques attackers use to **maintain access** to a Linux system after initial compromise.

From a SOC and DFIR perspective, persistence is critical because:
- It allows attackers to survive reboots
- It enables long-term access for lateral movement or data exfiltration
- It often blends with legitimate system behavior

Detecting persistence is often the **key to fully eradicating an intrusion**.

---

## 🧱 Why Persistence Is Common on Linux
Attackers favor Linux persistence because:
- Linux provides many legitimate startup mechanisms
- Configuration files are often trusted and overlooked
- Misconfigurations are common in servers and cloud environments

Persistence rarely requires exploits once initial access is gained.

---

## 🔑 Common Linux Persistence Mechanisms

## 1️⃣ Cron Jobs
Cron allows scheduled execution of commands.

Common locations:
- `/etc/crontab`
- `/etc/cron.d/`
- `/var/spool/cron/`
- User crontabs

### SOC Relevance
- Cron jobs running shells or download commands are suspicious
- Recently created cron entries after compromise are high-risk

---

## 2️⃣ systemd Services (Most Common)
Modern Linux systems use `systemd` for service management.

Persistence methods:
- Malicious `.service` files
- Modified existing services
- User-level systemd services

Common paths:
- `/etc/systemd/system/`
- `/lib/systemd/system/`
- `~/.config/systemd/user/`

### SOC Relevance
- New or modified services executing scripts or shells
- Services running from non-standard paths
- User-level services providing stealthy persistence

---

## 3️⃣ Init Scripts (Legacy)
Older systems may use SysVinit scripts.

Common paths:
- `/etc/init.d/`
- `/etc/rc.local`

### SOC Relevance
- Rarely used legitimately on modern systems
- Presence may indicate persistence or legacy misconfiguration

---

## 4️⃣ SSH Authorized Keys
Attackers add their public keys for passwordless access.

Common location:
- `~/.ssh/authorized_keys`

### SOC Relevance
- New keys added to existing users
- Keys added to privileged accounts (root, sudo users)

---

## 5️⃣ Bash Profile and Shell Startup Files
Shell startup files execute commands when a shell starts.

Common files:
- `~/.bashrc`
- `~/.bash_profile`
- `~/.profile`
- `/etc/profile`

### SOC Relevance
- Hidden or obfuscated commands
- Network or execution logic in shell profiles

---

## 6️⃣ System-Wide Startup Files
Some distributions execute scripts at boot.

Examples:
- `/etc/rc.local`
- Custom scripts referenced by services

### SOC Relevance
- Rare in modern environments
- High-confidence persistence indicator when present

---

## 7️⃣ LD_PRELOAD and Environment-Based Persistence
Attackers abuse environment variables to hijack execution.

Examples:
- `LD_PRELOAD`
- `LD_LIBRARY_PATH`

### SOC Relevance
- Stealthy and difficult to detect
- Often used for privilege escalation and persistence

---

## 🚨 High-Risk Persistence Patterns
SOC analysts should treat the following as high risk:
- Persistence pointing to `/tmp`, `/var/tmp`, or user home directories
- Use of `curl`, `wget`, or `bash` in persistence logic
- Obfuscated or encoded commands
- Multiple persistence layers on the same host

---

## 📊 What SOC Analysts Should Monitor
High-value telemetry includes:
- Creation or modification of cron jobs
- systemd service file changes
- SSH authorized_keys modifications
- Changes to shell startup files
- Unexpected environment variable usage

Correlation with initial execution events is critical.

---

## 🧩 MITRE ATT&CK Mapping
Linux persistence techniques map to:
- Persistence
- Privilege Escalation
- Defense Evasion

---

## 🧪 Real-World Persistence Example
1. Attacker gains user shell via SSH
2. Adds cron job executing `curl | bash`
3. Installs systemd service as backup
4. Adds SSH key for passwordless access
5. Persistence survives reboot and password reset

Attackers often deploy **multiple persistence mechanisms**.

---

## 🧠 SOC Analyst Mindset
Always ask:
- How does this survive a reboot?
- Is this persistence legitimate for this system’s role?
- When was it created and by whom?
- Is there more than one persistence method?

Persistence answers usually reveal the attacker.

---

