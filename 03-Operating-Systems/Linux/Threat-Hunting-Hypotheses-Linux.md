# 🔍 Threat Hunting Hypotheses (Linux SOC)

## 📌 Overview
Threat hunting is a **proactive search for attacker behavior**
that has evaded automated detection.

This document provides **Linux-focused hunting hypotheses**
based on real-world attacker techniques.

---

## 🎯 How to Use These Hypotheses
Each hypothesis:
- States an attacker assumption
- Identifies data sources
- Suggests what to look for

Hunting is about **questions**, not alerts.

---

## 🧠 Hypothesis 1: Compromised SSH Access Exists
Attackers may have valid SSH access.

Look for:
- SSH logins from unusual IPs
- Successful logins without failures
- SSH followed by immediate sudo

Data sources:
- Auth logs
- sudo logs

---

## 🧠 Hypothesis 2: Persistence Exists on the Host
Attackers often deploy persistence.

Look for:
- Cron jobs executing shells
- systemd services running from writable paths
- New SSH keys

Data sources:
- Cron configs
- systemd units
- File integrity monitoring

---

## 🧠 Hypothesis 3: Fileless Malware Is Running
Attackers avoid writing files.

Look for:
- `curl | bash` patterns
- Shells with network connections
- Processes without corresponding binaries

Data sources:
- Process telemetry
- Network logs

---

## 🧠 Hypothesis 4: Lateral Movement Is Underway
Attackers move between systems.

Look for:
- Same user authenticating to many hosts
- SSH key reuse
- Internal SSH connections outside norms

Data sources:
- Auth logs across hosts
- Network telemetry

---

## 🧠 Hypothesis 5: Anti-Forensics Has Occurred
Attackers may be hiding evidence.

Look for:
- Missing logs
- Timeline gaps
- Root activity without history

Data sources:
- Logs
- File metadata
- Audit data

---

## 🧠 Hypothesis 6: Containers Are Abused
Attackers abuse container platforms.

Look for:
- Containers running as root
- Docker socket access
- Unexpected container creation

Data sources:
- Docker logs
- Host process data

---

## 🧠 SOC Hunter Mindset
Always ask:
- What *should* be happening here?
- What is missing?
- What changed recently?
- Does this behavior scale across hosts?

Threat hunting turns **unknown unknowns** into findings.

---

## 🚀 Outcome
Effective threat hunting:
- Finds silent compromises
- Improves detections
- Reduces dwell time
- Raises SOC maturity
