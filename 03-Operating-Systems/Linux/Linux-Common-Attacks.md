# ⚔️ Linux Common Attacks (SOC & DFIR)

## 📌 Overview
Linux systems are frequently targeted in:
- Servers
- Cloud environments
- Containers
- CI/CD infrastructure

Most Linux attacks rely on **misconfigurations and native tools**, not malware.

---

## 🧱 Typical Linux Attack Lifecycle
1. Initial Access
2. Execution
3. Persistence
4. Privilege Escalation
5. Credential Access
6. Lateral Movement
7. Defense Evasion
8. Impact

SOC analysts focus on **behavior**, not tools.

---

## 🔓 Initial Access

### Common Techniques
- SSH brute force
- Compromised credentials
- Exploiting public-facing services

### SOC Indicators
- Repeated SSH failures
- Successful login after failures
- Logins from unusual IPs

---

## ▶️ Execution

### Common Techniques
- Bash or shell execution
- Script execution
- Living-off-the-land binaries

### SOC Indicators
- Shells spawned by SSH or services
- Download-and-execute patterns

---

## ♻️ Persistence
- Cron jobs
- systemd services
- SSH keys
- Shell profiles

SOC focus: persistence created soon after access.

---

## ⬆️ Privilege Escalation
- sudo misconfigurations
- SUID binaries
- Capabilities abuse
- Kernel exploits

SOC focus: transition to UID 0.

---

## 🔐 Credential Access
- SSH key harvesting
- Config file scraping
- Environment secrets

SOC focus: access to `.ssh` and config files.

---

## 🌐 Lateral Movement
- SSH credential reuse
- Agent forwarding
- Shared storage abuse

SOC focus: authentication spread.

---

## 🛡️ Defense Evasion
- Log deletion
- Obfuscation
- Masquerading processes

SOC focus: missing telemetry.

---

## 💥 Impact
- Data destruction
- Crypto-mining
- Service disruption

SOC focus: performance anomalies.

---

## 🧩 MITRE ATT&CK Mapping
Linux common attacks span:
- Initial Access
- Execution
- Persistence
- Privilege Escalation
- Credential Access
- Lateral Movement
- Defense Evasion
- Impact
