# 👤 Windows Logon Types & Sessions

## 📌 Why Logon Types Matter
Event **4624 (Successful Logon)** is meaningless without understanding:
- Logon Type
- Source
- Account

80% of SOC alerts depend on this context.

---

## 🔢 Common Logon Types

| Logon Type | Description | SOC Meaning |
|-----------:|------------|-------------|
| **2** | Interactive | Physical or console login |
| **3** | Network | SMB, file access, lateral movement |
| **4** | Batch | Scheduled tasks |
| **5** | Service | Services starting |
| **7** | Unlock | Session unlock |
| **10** | RemoteInteractive | RDP |
| **11** | CachedInteractive | Offline login |

<img width="800" height="1150" alt="image" src="https://github.com/user-attachments/assets/80daf24e-1e02-4653-b826-c58fcc601c57" />


<img width="626" height="954" alt="image" src="https://github.com/user-attachments/assets/2aa5c744-d976-476a-abc7-c313f1d074a5" />

---

## 🚨 High-Risk Patterns
- Logon Type 3 from user workstation → server
- Logon Type 10 outside business hours
- Service logons using user accounts

---

## 🧠 SOC Detection Tips
- Always correlate: Logon Type + Source Host + Account
- One login ≠ compromise, patterns do

---

## 🧩 MITRE Mapping
- Lateral Movement
- Persistence
- Credential Access
