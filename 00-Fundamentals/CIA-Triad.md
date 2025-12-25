# CIA Triad

The **CIA Triad** is a foundational cybersecurity model that defines the **three core principles** security teams aim to protect:

- **Confidentiality**
- **Integrity**
- **Availability**

<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/8a22c85b-069b-4562-a5a0-169a58c03302" />


Every security incident investigated in a SOC impacts **one or more** of these principles.

---

## 🔐 Confidentiality
Ensures that information is **accessible only to authorized users**.

### Examples of Confidentiality Violations
- Data breaches
- Unauthorized file access
- Credential theft
- Insider threats

### SOC Indicators
- Access to sensitive files outside job role
- Unusual login locations
- Privileged account misuse

### SOC Goal
Detect and stop **unauthorized access** before data is exposed.

---

## 🧾 Integrity
Ensures that data is **accurate, complete, and unaltered**.

### Examples of Integrity Violations
- File tampering
- Log manipulation
- Malware modifying system files
- Unauthorized configuration changes

### SOC Indicators
- Unexpected file changes
- Disabled logging
- Hash mismatches
- Registry modifications

### SOC Goal
Detect **unauthorized changes** and identify the source.

---

## ⚙️ Availability
Ensures that systems and data are **available when needed**.

### Examples of Availability Violations
- Denial of Service (DoS / DDoS)
- Ransomware
- System crashes
- Resource exhaustion

### SOC Indicators
- Service outages
- High CPU or memory usage
- Systems becoming unreachable
- Alert storms

### SOC Goal
Restore services quickly and reduce downtime.

---

## 🧠 CIA Triad from a SOC Perspective
SOC analysts do not just ask:
> “Was this malicious?”

They ask:
- Which CIA principle was affected?
- How severe is the impact?
- What is the business risk?

This helps determine:
- Incident severity
- Escalation priority
- Response urgency

---

## 🔁 CIA Triad & Incident Severity

| CIA Element | Impact Example | Severity |
|-----------|---------------|---------|
| Confidentiality | Data leak | High |
| Integrity | Log tampering | High |
| Availability | Short outage | Medium |
| Availability | Ransomware | Critical |

---

## 🔗 Practice Mapping
CIA Triad analysis is used in:
- Incident classification
- Risk assessment
- Executive reporting
- Case study impact analysis
