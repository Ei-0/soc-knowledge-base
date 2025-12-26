# 🔐 Windows Authentication Internals

## 📌 Overview
Windows authentication is the foundation of **identity, access, and trust** in enterprise environments.

For SOC analysts, understanding authentication internals explains:
- How credentials are validated
- Where credentials live
- Why Kerberos and NTLM attacks work
- How to interpret authentication logs correctly

Without this knowledge, many alerts become guesswork.

---

## 🧱 Core Authentication Components

### 🔹 LSASS (Local Security Authority Subsystem Service)
LSASS is responsible for:
- User authentication
- Credential validation
- Token generation

🔍 SOC View:
- LSASS memory is a prime target
- Credential dumping almost always targets LSASS

---

### 🔹 Authentication Packages
Windows supports multiple authentication mechanisms:
- NTLM
- Kerberos
- Credential Manager

Each leaves **different artifacts and logs**.

---

## 🔑 NTLM Authentication
NTLM is a **challenge–response** protocol.

Characteristics:
- Uses password hashes
- No mutual authentication
- Still widely used internally

🔍 SOC Indicators:
- NTLM usage in modern domains is suspicious
- Often used in lateral movement

---

## 🎟️ Kerberos Authentication
Kerberos is the default authentication protocol in Active Directory.

Key concepts:
- Tickets (TGT, TGS)
- Domain Controller (KDC)
- Mutual authentication

🔍 SOC Indicators:
- Abnormal ticket usage
- Kerberos events without user interaction

---

## 🧠 Where Credentials Live
Credentials may exist in:
- LSASS memory
- Cached credentials
- Kerberos tickets
- NTLM hashes

SOC analysts should assume **credentials are stolen before lateral movement**.

---

## 🚨 SOC Detection Ideas
- LSASS access attempts
- NTLM authentication in Kerberos environments
- Abnormal authentication sources
- Ticket reuse across hosts

---

## 🧩 MITRE ATT&CK Mapping
- Credential Access
- Lateral Movement
- Defense Evasion

---

## 🚀 What’s Next?
👉 Windows Logon Types & Sessions
