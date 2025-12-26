# ⏰ Cron Persistence (Linux) — SOC & DFIR

## 📌 Overview
Cron is a Linux scheduling service used to run commands at fixed times or intervals.

From a SOC and DFIR perspective, **cron is one of the most abused persistence mechanisms** because:
- It is legitimate and widely used
- It survives reboots
- It can execute commands as root or specific users
- It often receives little monitoring

If an attacker has user access, cron is usually one of the **first persistence options**.

---

## 🧱 How Cron Works (Quick Recap)
Cron executes jobs defined in:
- System-wide cron files
- Per-user crontabs

Execution context depends on:
- The user owning the cron job
- The command specified
- Environment variables at runtime

---

## 📂 Cron Locations (High-Value)

### System-Wide Cron
- `/etc/crontab`
- `/etc/cron.d/`
- `/etc/cron.hourly/`
- `/etc/cron.daily/`
- `/etc/cron.weekly/`
- `/etc/cron.monthly/`

### User Cron
- `/var/spool/cron/`
- User-specific crontabs (managed via `crontab -e`)

SOC note:
- System cron often runs as **root**
- User cron provides stealthy user-level persistence

---

## 🔑 Common Cron Persistence Techniques

### 1️⃣ Download-and-Execute
Attackers schedule cron jobs to fetch payloads.

Example pattern:
- `curl | bash`
- `wget | sh`

SOC relevance:
- Network activity initiated by cron
- Commands rarely used by legitimate cron jobs

---

### 2️⃣ Script Execution
Cron runs a local script repeatedly.

Example:
- Script stored in `/tmp`, `/var/tmp`, or home directory

SOC relevance:
- Executables in writable directories
- Persistence tied to non-standard paths

---

### 3️⃣ Reverse Shell Cron Jobs
Cron periodically opens outbound connections.

SOC relevance:
- Regular outbound connections at fixed intervals
- Network beacons aligned with cron schedule

---

### 4️⃣ Obfuscated Cron Entries
Attackers hide commands using:
- Base64 encoding
- Environment variables
- Indirect execution (`sh -c`, `eval`)

SOC relevance:
- Cron entries that are hard to read
- Encoded or chained commands

---

### 5️⃣ Root Cron Abuse
If attackers gain root or writable access to root cron:
- Full system persistence is achieved

SOC relevance:
- Any modification to root cron is **critical severity**

---

## 🚨 High-Risk Cron Indicators
Treat the following as high-risk:
- Cron jobs created shortly after SSH access
- Cron executing shells or interpreters
- Cron referencing `/tmp`, `/var/tmp`, or hidden files
- Cron jobs owned by users that normally do not use cron
- Multiple cron jobs used as backup persistence

---

## 📊 What SOC Analysts Should Monitor
High-value telemetry:
- Creation or modification of cron files
- Cron execution logs
- Network activity initiated by cron
- Correlation between SSH login → cron creation

Useful log sources:
- `/var/log/syslog`
- `/var/log/cron` (RHEL-based)
- systemd journal

---

## 🧩 MITRE ATT&CK Mapping
Cron persistence maps to:
- Persistence
- Execution
- Defense Evasion

---

## 🧪 Real-World Cron Persistence Example
1. Attacker gains SSH access as user
2. Adds cron job executing `curl | bash` every 5 minutes
3. Payload installs backdoor
4. Cron ensures backdoor is reinstalled if removed
5. Persistence survives reboot and cleanup attempts

Cron acts as a **self-healing mechanism** for attackers.

---

## 🧠 SOC Analyst Mindset
Always ask:
- Why does this user need a cron job?
- What does this cron job execute?
- When was it created?
- Is this aligned with the system’s role?

On Linux servers, **cron should be boring**.  
Anything clever is suspicious.

---
