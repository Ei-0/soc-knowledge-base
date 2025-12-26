# ⬆️ Privilege Escalation (Windows)

<img width="750" height="276" alt="image" src="https://github.com/user-attachments/assets/7bcc3359-e028-4cff-af97-797299c65ece" />

## 📌 Overview
**Privilege Escalation** is the process of gaining higher permissions than initially granted.

For attackers, this usually means:
- User → Administrator
- Administrator → SYSTEM

For SOC analysts, this is a **critical kill-chain stage**.

---

## 🧱 Types of Privilege Escalation

### 🔹 Vertical Escalation
- Standard user → Admin/SYSTEM

### 🔹 Horizontal Escalation
- One user → Another user

---

## 🚨 Common Windows Privilege Escalation Techniques

### 🔹 Exploiting Vulnerable Drivers
Attackers load signed but vulnerable drivers to:
- Execute kernel code
- Disable security tools

🔍 SOC Indicators:
- New driver loads
- Unusual driver paths

---

### 🔹 Token Manipulation
Abusing access tokens to:
- Impersonate privileged users
- Steal SYSTEM tokens

🔍 SOC Indicators:
- Sudden privilege changes
- SYSTEM actions from user processes

---

### 🔹 UAC Bypass
Attackers bypass elevation prompts.

🔍 SOC Indicators:
- Elevated actions without user consent
- Registry or auto-elevated binaries abuse

---

### 🔹 Service Misconfigurations
Abusing:
- Weak service permissions
- Writable service binaries

🔍 SOC Indicators:
- Service binary replacement
- Permission changes

---

## 📊 What SOC Analysts Should Monitor
- Privilege assignment events
- Admin group membership changes
- Driver installations
- Service permission changes

---

## 🧩 MITRE ATT&CK Mapping
- Privilege Escalation
- Defense Evasion

---

## 🚀 What’s Next?
👉 **Lateral-Movement.md**
