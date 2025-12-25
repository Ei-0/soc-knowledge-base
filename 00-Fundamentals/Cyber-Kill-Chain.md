# Cyber Kill Chain

The **Cyber Kill Chain** is a model that describes the **stages of a cyber attack**, from initial planning to achieving the attacker’s objective.

It helps SOC analysts understand:
- Where an attack is happening
- What evidence to look for
- How to stop the attack as early as possible

---

## 🔗 What Is the Cyber Kill Chain?
The model was developed by **:contentReference[oaicite:0]{index=0}** and is widely used in defensive security operations.

The goal is simple:
> **Break the attack chain before the attacker succeeds**

---

## 🧩 Cyber Kill Chain Stages

<img width="1159" height="612" alt="image" src="https://github.com/user-attachments/assets/214f61ab-0bbc-42fb-9516-a3142db87e82" />


### 1️⃣ Reconnaissance
Attacker gathers information about the target.

**Examples**
- Scanning IP ranges
- Collecting employee emails
- Identifying technologies in use

**SOC Visibility**
- Network scans
- Suspicious DNS queries
- OSINT indicators

---

### 2️⃣ Weaponization
Attacker prepares the payload.

**Examples**
- Malware creation
- Weaponized documents
- Exploit kits

**SOC Visibility**
- Limited (often happens offline)
- Threat intelligence feeds may help

---

### 3️⃣ Delivery
Payload is delivered to the target.

**Examples**
- Phishing emails
- Malicious links
- USB devices

**SOC Visibility**
- Email security logs
- Web proxy logs
- Attachment analysis

---

### 4️⃣ Exploitation
The payload executes by exploiting a vulnerability.

**Examples**
- Macro execution
- Browser exploit
- Software vulnerability abuse

**SOC Visibility**
- EDR alerts
- Application crash logs
- Script execution logs

---

### 5️⃣ Installation
Malware installs persistence mechanisms.

**Examples**
- Registry run keys
- Scheduled tasks
- Services creation

**SOC Visibility**
- Registry changes
- New services
- Persistence artifacts

---

### 6️⃣ Command and Control (C2)
Infected system communicates with attacker infrastructure.

**Examples**
- Periodic beaconing
- Encrypted outbound traffic
- DNS tunneling

**SOC Visibility**
- Network traffic anomalies
- Suspicious domains/IPs
- Beaconing patterns

---

### 7️⃣ Actions on Objectives
Attacker achieves their goal.

**Examples**
- Data exfiltration
- Lateral movement
- Ransomware deployment

**SOC Visibility**
- Large data transfers
- Privilege escalation
- File access anomalies

---

## 🛑 SOC Analyst Perspective
The earlier you detect an attack in the kill chain:
- The less damage occurs
- The easier containment becomes
- The lower the recovery cost

SOC teams aim to detect attacks **before stage 6 or 7**.

---

## 🔁 Kill Chain vs Modern Frameworks
While the Cyber Kill Chain is useful, modern SOCs often complement it with **:contentReference[oaicite:1]{index=1}**, which focuses on **attacker behavior and techniques** rather than linear stages.

---

## 🔗 Practice Mapping
This model is applied in:
- Incident investigations
- Timeline analysis
- Case studies (mapping attacker progress)
