# ⚡ Windows PowerShell Security

## 📌 Why PowerShell Matters
PowerShell is the **backbone of modern Windows attacks**.

Attackers use it for:
- Initial execution
- Fileless malware
- Lateral movement
- Persistence

---

## 🔍 Key Security Features

### 🔹 Script Block Logging
Logs actual script content.

### 🔹 AMSI
Scans scripts before execution.

---

## 🚨 Common Abuse Techniques
- Encoded commands
- Obfuscation
- Living-off-the-land

---

## 📊 SOC Detection Ideas
- PowerShell with Base64
- Download + Execute patterns
- PowerShell spawned by Office apps

---

## 🧩 MITRE Mapping
- Execution
- Defense Evasion
