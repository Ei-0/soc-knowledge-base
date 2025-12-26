# 🌐 Lateral Movement (Windows)

## 📌 Overview
**Lateral Movement** allows attackers to move from one compromised system to others inside the network.

For SOC teams, detecting lateral movement is often the **difference between a contained incident and a full breach**.

<img width="1838" height="938" alt="image" src="https://github.com/user-attachments/assets/0de172a6-2fba-4064-a887-791442e6faa6" />

---

## 🧱 Why Lateral Movement Matters
Attackers move laterally to:
- Reach high-value systems
- Access sensitive data
- Gain domain dominance

---

## 🚨 Common Lateral Movement Techniques

### 🔹 Pass-the-Hash
Uses stolen NTLM hashes to authenticate.

🔍 SOC Indicators:
- Logins without password usage
- Authentication from unusual hosts

---

### 🔹 Pass-the-Ticket
Abuses Kerberos tickets.

🔍 SOC Indicators:
- Kerberos anomalies
- Ticket reuse across systems

---

### 🔹 Remote Services
Attackers use:
- SMB
- RDP
- WMI
- PsExec

🔍 SOC Indicators:
- Admin logins across multiple systems
- Service creation on remote hosts

---

### 🔹 Credential Reuse
Using the same credentials across systems.

🔍 SOC Indicators:
- Same account authenticating to many hosts

---

## 📊 What SOC Analysts Should Monitor
- Authentication logs (4624 / 4768 / 4769)
- Source/destination host patterns
- Remote service creation
- Admin session spread

---

## 🧩 Mapping to MITRE ATT&CK
- Lateral Movement
- Credential Access
- Privilege Escalation

---

## 🧪 Example Attack Path
1. Initial access on workstation
2. Credentials dumped
3. Lateral movement to file server
4. Admin access obtained
5. Domain controller targeted

---

