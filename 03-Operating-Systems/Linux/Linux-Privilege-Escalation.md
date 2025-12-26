# ⬆️ Linux Privilege Escalation (SOC & DFIR)

## 📌 Overview
Privilege Escalation on Linux is the process of gaining **higher privileges** than initially granted, usually moving from:
- Normal user → root (UID 0)

From a SOC and DFIR perspective, privilege escalation is a **critical turning point**:
- Before escalation: limited impact
- After escalation: full system control

Most Linux compromises aim for root access.

---

## 🧱 Why Privilege Escalation Works on Linux
Attackers succeed due to:
- Misconfigurations
- Overly permissive sudo rules
- Vulnerable or custom binaries
- Weak file permissions
- Legacy configurations

Privilege escalation often requires **no exploits**, just abuse.

---

## 🔑 Common Linux Privilege Escalation Techniques

## 1️⃣ Misconfigured sudo
`sudo` allows users to execute commands as root.

High-risk configurations:
- Passwordless sudo
- Allowing shells or editors
- Wildcards in sudo rules

### SOC Relevance
- Unexpected sudo usage is a strong indicator
- `sudo` + shell = full compromise

---

## 2️⃣ SUID Binaries
SUID binaries run with the **owner’s privileges**.

Common abuse:
- Writable SUID binaries
- Custom or uncommon SUID files
- GTFOBins abuse

### SOC Relevance
- Changes to SUID permissions are critical alerts
- Execution of uncommon SUID binaries is suspicious

---

## 3️⃣ Writable Files Owned by Root
If a root-owned executable or script is writable:
- Attacker can modify it
- Code executes as root later

### SOC Relevance
- World-writable or group-writable root files are extremely dangerous
- Often lead to persistence + escalation

---

## 4️⃣ Linux Capabilities Abuse
Capabilities split root privileges into granular permissions.

Examples:
- `CAP_SYS_ADMIN`
- `CAP_SETUID`

### SOC Relevance
- Capabilities on scripting engines (python, perl) are high risk
- Often overlooked during audits

---

## 5️⃣ Cron Jobs & Scheduled Tasks
If cron jobs run as root and reference writable files:
- Attacker can replace the file
- Code runs as root automatically

### SOC Relevance
- Writable scripts executed by root cron jobs
- New cron jobs shortly after compromise

---

## 6️⃣ Environment Variable Abuse
Attackers manipulate:
- `PATH`
- `LD_PRELOAD`
- `LD_LIBRARY_PATH`

### SOC Relevance
- Execution hijacking without touching binaries
- Stealthy and difficult to detect

---

## 7️⃣ Kernel Exploits (Less Common, High Impact)
Exploiting kernel vulnerabilities to gain root.

### SOC Relevance
- Rare but extremely high impact
- Often noisy (crashes, instability)

---

## 🚨 High-Risk Privilege Escalation Indicators
SOC analysts should treat these as critical:
- Sudden UID change to 0
- Root shells spawned by user processes
- New SUID binaries
- sudo usage outside normal patterns
- Capability changes

---

## 📊 What SOC Analysts Should Monitor
High-value signals:
- sudo execution logs
- UID/GID transitions
- SUID permission changes
- Cron jobs running as root
- Capability assignments
- Root-owned file modifications

Correlation with initial access is key.

---

## 🧩 MITRE ATT&CK Mapping
Linux privilege escalation maps to:
- Privilege Escalation
- Defense Evasion
- Persistence

---

## 🧪 Real-World Privilege Escalation Example
1. Attacker gains user shell via SSH
2. Discovers passwordless sudo for `vim`
3. Spawns root shell via editor
4. Installs persistence as root
5. Full system compromise achieved

---

## 🧠 SOC Analyst Mindset
Always ask:
- How did this user gain root?
- Was this configuration intentional?
- Could this be abused again?
- Is persistence already installed?

Privilege escalation explains **how the attacker truly won**.

---

