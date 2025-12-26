# 🔐 Linux SSH Security (SOC & DFIR)

## 📌 Overview
SSH (Secure Shell) is the **primary remote access mechanism** for Linux systems.

From a SOC and DFIR perspective, SSH security is critical because:
- The majority of Linux compromises start with SSH
- SSH is used for initial access, persistence, and lateral movement
- Misconfigurations and key abuse are extremely common

If SSH is weak, the entire Linux environment is weak.

---

## 🧱 How SSH Works (Security Context)
SSH provides:
- Encrypted remote access
- Authentication via passwords or keys
- Port forwarding and tunneling

Authentication methods:
- Password-based authentication
- Public key authentication
- Keyboard-interactive (via PAM)

SOC relevance:
- Each method leaves different log artifacts
- Key-based attacks are harder to detect than passwords

---

## 🔑 SSH Authentication Methods & Risks

### Password Authentication
Risks:
- Brute force attacks
- Password reuse
- Credential stuffing

SOC indicators:
- Repeated failed logins
- Successful login after many failures
- Multiple users targeted from one IP

---

### SSH Key-Based Authentication
Risks:
- Stolen private keys
- Weak key protection
- Key reuse across systems

SOC indicators:
- Successful logins without prior failures
- Same key fingerprint used on multiple hosts
- New keys added shortly after compromise

---

## 📂 Authorized Keys Abuse
Attackers often add their own SSH keys for persistence.

Location:
- `~/.ssh/authorized_keys`

SOC indicators:
- New keys added to privileged accounts
- Keys added outside maintenance windows
- Identical keys across multiple systems

---

## 🔁 SSH Agent Forwarding Abuse
If agent forwarding is enabled:
- Attacker can authenticate to other systems without stealing keys
- Enables stealthy lateral movement

SOC indicators:
- SSH logins without local private key usage
- Lateral movement with no new credentials created

---

## 🔀 SSH Port Forwarding & Tunneling
SSH can forward ports locally or remotely.

Abuse cases:
- Bypassing firewalls
- Hiding C2 traffic
- Pivoting inside networks

SOC indicators:
- SSH sessions with port forwarding enabled
- Internal services accessed through SSH tunnels

---

## ⚙️ SSH Configuration Weaknesses
Key configuration file:
- `/etc/ssh/sshd_config`

High-risk settings:
- `PermitRootLogin yes`
- `PasswordAuthentication yes`
- `AllowAgentForwarding yes`
- Weak ciphers or key lengths

SOC relevance:
- Changes to SSH config may indicate attacker hardening access

---

## 🧱 Root Login via SSH
Allowing root SSH access increases risk:
- Direct full control
- Fewer forensic breadcrumbs

SOC indicators:
- Root SSH logins
- Root access from non-management IPs

---

## 🚨 High-Risk SSH Indicators
Treat these as critical:
- SSH login followed immediately by sudo
- SSH access outside normal hours
- SSH logins from unexpected locations
- Key-based logins where passwords were expected
- SSH used between servers without justification

---

## 📊 What SOC Analysts Should Monitor
High-value telemetry:
- SSH authentication logs
- Source IP addresses
- Usernames and accounts
- Authentication method used
- Session duration and frequency
- SSH usage between internal hosts

Correlation across hosts is essential.

---

## 🧩 MITRE ATT&CK Mapping
SSH abuse maps to:
- Initial Access
- Persistence
- Credential Access
- Lateral Movement
- Command and Control

---

## 🧪 Real-World SSH Attack Example
1. Attacker brute-forces SSH credentials
2. Successful login as valid user
3. Adds SSH key to `authorized_keys`
4. Uses agent forwarding to pivot internally
5. Maintains long-term access without passwords

SSH becomes both the **entry point and the highway**.

---

## 🧠 SOC Analyst Mindset
Always ask:
- Should this user be using SSH?
- Is this source IP expected?
- Why is SSH being used between these hosts?
- Did SSH access lead to persistence or escalation?

On Linux, **SSH logs often tell the whole story**.

---
