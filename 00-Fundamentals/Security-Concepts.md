# Core Security Concepts

This document explains **core cybersecurity concepts** every SOC analyst must understand.
These concepts are used daily when analyzing alerts, incidents, and risks.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dab3a7bc-6f2f-481f-be76-01c99b831cd2" />

---

## 🎯 Threat
A **threat** is anything that has the potential to cause harm.

### Examples
- Malware
- Insider threats
- External attackers
- Misconfigured systems

### SOC Perspective
Threats represent **intent or capability**, not necessarily exploitation.

---

## 🕳️ Vulnerability
A **vulnerability** is a weakness that can be exploited by a threat.

### Examples
- Unpatched software
- Weak passwords
- Misconfigurations
- Excessive privileges

### SOC Perspective
SOC analysts monitor alerts that may indicate **vulnerability exploitation**.

---

## ⚠️ Risk
**Risk** is the potential impact when a threat exploits a vulnerability.

> Risk = Threat × Vulnerability × Impact

### Examples
- Exposed admin account + phishing = high risk
- Unpatched server + internet exposure = critical risk

### SOC Perspective
Risk determines:
- Incident severity
- Escalation priority
- Response urgency

---

## 🧨 Attack
An **attack** is the active exploitation of a vulnerability by a threat.

<img width="1024" height="576" alt="image" src="https://github.com/user-attachments/assets/24f7baf4-33f4-4f8c-aca1-a0a9cd6dc159" />

### Examples
- Credential theft
- Malware execution
- Lateral movement
- Data exfiltration

### SOC Perspective
Attacks are what SOC analysts **detect, investigate, and respond to**.

---

## 🧩 Attack Surface
The **attack surface** is the total number of points an attacker can target.

### Examples
- Open ports
- Internet-facing services
- User accounts
- APIs and web applications

### SOC Perspective
A larger attack surface means:
- More alerts
- More investigation work
- Higher likelihood of compromise

---

## 🛡️ Controls
**Security controls** are measures used to reduce risk.

### Types of Controls
- Preventive (firewalls, MFA)
- Detective (SIEM, EDR)
- Corrective (incident response, patching)

### SOC Perspective
SOC primarily operates **detective and corrective controls**.

---

## 🔄 Defense in Depth
**Defense in Depth** uses multiple layers of security controls.

<img width="1412" height="755" alt="image" src="https://github.com/user-attachments/assets/41142bf2-7a7b-49c1-a6bb-66cba048871a" />


### Examples
- Firewall + EDR + SIEM
- MFA + monitoring + logging

### SOC Perspective
When one control fails, others provide **visibility and detection**.

---

## 🧠 How SOC Analysts Use These Concepts
During investigations, SOC analysts ask:
- What is the threat?
- What vulnerability was exploited?
- What is the risk and business impact?
- Which CIA principle is affected?
- How can we reduce this risk in the future?

These concepts also align with behavior-based frameworks such as **:contentReference[oaicite:0]{index=0}**.

---

## 🔗 Practice Mapping
These concepts are applied in:
- Alert triage
- Incident severity classification
- Threat hunting hypotheses
- Lessons learned from case studies
