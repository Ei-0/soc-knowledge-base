# Incident Severity & Classification

Incident severity classification helps SOC teams **prioritize response** based on risk and business impact.

---

## 🎯 Why Severity Matters
- Not all incidents are equal
- Resources are limited
- Business impact varies

Severity determines:
- Escalation level
- Response urgency
- Management involvement

---

## 🚦 Common Severity Levels

<img width="1024" height="1536" alt="image" src="https://github.com/user-attachments/assets/b473874f-dfc4-4387-82c7-5c7b8fab5103" />

### 🟢 Low
Examples:
- Failed login attempts
- Scanning activity
- Benign anomalies

Response:
- Monitor
- Document
- No escalation

---

### 🟡 Medium
Examples:
- Malware blocked
- Suspicious PowerShell execution
- Credential misuse attempts

Response:
- Investigate
- Contain if needed
- Possible escalation

---

### 🔴 High
Examples:
- Confirmed malware execution
- Lateral movement
- Privilege escalation

Response:
- Immediate containment
- Escalate to IR team
- Evidence collection

---

### ⚫ Critical
Examples:
- Data exfiltration
- Ransomware
- Domain compromise

Response:
- Incident response activation
- Executive notification
- Full containment & recovery

---

## 🧠 How SOC Analysts Determine Severity
SOC analysts consider:
- CIA Triad impact
- Scope of compromise
- Attacker intent
- Business criticality

---

## 🔗 Practice Mapping
Severity classification is used in:
- Alert triage
- Incident escalation
- SOC metrics (MTTD / MTTR)
- Case study reporting
