# Pyramid of Pain

The **Pyramid of Pain** is a cybersecurity concept that shows **how difficult it is for attackers to change different indicators** once they are detected.

It helps SOC analysts understand:
- Which detections hurt attackers the most
- Why behavior-based detection is superior
- How to prioritize detection engineering efforts

---

## 🧠 What Is the Pyramid of Pain?
The Pyramid of Pain was introduced by **:contentReference[oaicite:0]{index=0}**.

The core idea:
> **The higher you detect on the pyramid, the more pain you cause the attacker.**

---

<img width="1280" height="898" alt="image" src="https://github.com/user-attachments/assets/29a42d13-1443-42a6-992b-9e2e1c80af99" />

## 🧱 Pyramid Levels (Bottom → Top)

### 1️⃣ Hash Values (Low Pain)
Examples:
- File hashes (MD5, SHA1, SHA256)

Why Low Pain:
- Attackers can easily recompile malware
- Hash changes instantly

SOC Usage:
- Basic malware detection
- IOC enrichment

---

### 2️⃣ IP Addresses
Examples:
- Malicious IPs
- C2 server IPs

Why Low Pain:
- Attackers can switch infrastructure quickly
- Cloud hosting makes rotation easy

SOC Usage:
- Network blocking
- Enrichment & context

---

### 3️⃣ Domain Names
Examples:
- Malicious domains
- Phishing domains
- C2 domains

Why Medium Pain:
- Requires attacker to register new domains
- Leaves infrastructure traces

SOC Usage:
- DNS monitoring
- Proxy and firewall detections

---

### 4️⃣ Network / Host Artifacts
Examples:
- Registry keys
- File paths
- Scheduled tasks
- Named pipes
- Mutexes

Why High Pain:
- Tightly coupled to malware functionality
- Changing them may break the attack

SOC Usage:
- EDR detections
- Host-based monitoring
- Persistence detection

---

### 5️⃣ Tools
Examples:
- Mimikatz
- Cobalt Strike
- PsExec
- PowerShell abuse

Why Very High Pain:
- Tools are reused across campaigns
- Changing tools requires retraining attackers

SOC Usage:
- Tool-based detections
- LOLBins monitoring
- Command-line analysis

---

### 6️⃣ Tactics, Techniques, and Procedures (TTPs) – Highest Pain
Examples:
- Credential dumping techniques
- Lateral movement methods
- Persistence strategies

Why Maximum Pain:
- Hardest for attackers to change
- Represents attacker behavior and tradecraft

SOC Usage:
- Behavioral detection
- Threat hunting
- Detection engineering

This level strongly aligns with **:contentReference[oaicite:1]{index=1}**.

---

## 🧠 SOC Analyst Takeaway
Not all detections are equal.

SOC analysts should aim to:
- Move from IOC-based detection
- Toward **behavior and technique-based detection**

This results in:
- Fewer false positives
- Longer attacker disruption
- Stronger security posture

---

## 📊 Pyramid Level vs Detection Quality

| Pyramid Level | Detection Strength | Attacker Pain |
|-------------|------------------|--------------|
| Hash | Weak | Low |
| IP | Weak | Low |
| Domain | Medium | Medium |
| Artifacts | Strong | High |
| Tools | Very Strong | Very High |
| TTPs | Best | Maximum |

---

## 🔗 Practice Mapping
The Pyramid of Pain is applied in:
- Detection engineering
- Threat hunting
- MITRE ATT&CK mapping
- Case study analysis and lessons learned
