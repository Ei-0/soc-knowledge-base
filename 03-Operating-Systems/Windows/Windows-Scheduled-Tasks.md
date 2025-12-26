# ⏰ Windows Scheduled Tasks (Deep Dive)

## 📌 Overview
Scheduled Tasks are one of the **cleanest persistence mechanisms** in Windows.

<img width="901" height="524" alt="image" src="https://github.com/user-attachments/assets/ec217e7d-91e0-4620-ad1e-c12037bae616" />

Used by:
- Administrators
- Red Teams
- APT actors

---

## 🧱 Why Attackers Love Scheduled Tasks
- Legitimate by design
- Flexible triggers
- Survive reboots
- Hard to notice

---

## 🔄 Common Triggers
- At logon
- At startup
- On schedule
- On event

---

## 🚨 Abuse Patterns
- Tasks running PowerShell
- Encoded commands
- Tasks created shortly after compromise

---

## 📊 SOC Monitoring
- Event IDs: 4698 / 4702
- Task names and creators
- Execution context

---

## 🧩 MITRE Mapping
- Persistence
- Execution
