# 🚦 SIEM Alert Classification Methodology
## Low | Medium | High | Critical

## 🎯 Objective

This methodology enables SOC analysts to:
- Classify SIEM alerts consistently
- Reduce confusion and alert fatigue
- Make fast, defensible decisions
- Align alert severity with real risk
- Escalate only when justified

This is a **thinking framework**, not tool-specific logic.

---

## 🧠 Core Principle

> Alerts do not have severity.  
> **Context gives alerts severity.**

Never classify an alert based only on:
- Rule name
- Tool severity
- Gut feeling

Severity comes from **impact + confidence + scope**.

---

## 🧩 The 4 Core Dimensions of Alert Classification

Every SIEM alert must be evaluated across **four dimensions**:

1️⃣ Confidence (Is it really malicious?)  
2️⃣ Impact (What happens if it succeeds?)  
3️⃣ Scope (How big is it?)  
4️⃣ Stage (How far did the attacker get?)

Severity = combination of these four.

---

## 1️⃣ Confidence — How Sure Are We?

| Confidence Level | Indicators |
|----------------|-----------|
| Low | Single weak indicator, noisy rule |
| Medium | Multiple indicators, partial confirmation |
| High | Strong behavioral evidence |
| Very High | Confirmed compromise / verified activity |

**Questions to ask**
- Is this behavior normal for this user/host?
- Is there corroborating telemetry?
- Is this alert reproducible?

---

## 2️⃣ Impact — What Is at Risk?

| Impact Level | Examples |
|-------------|----------|
| Low | User workstation, no sensitive data |
| Medium | Business app, standard user |
| High | Server, sensitive data, admin account |
| Critical | Domain admin, cloud tenant, production systems |

**Impact is about potential damage — not detection quality.**

---

## 3️⃣ Scope — How Widespread Is It?

| Scope | Description |
|-----|------------|
| Single | One user or one host |
| Limited | Few users or systems |
| Broad | Multiple systems / departments |
| Enterprise | Org-wide / tenant-wide |

Scope increases severity **fast**.

---

## 4️⃣ Attack Stage — How Far Did It Go?

| Stage | Meaning |
|-----|--------|
| Attempted | Blocked or failed |
| Initial Access | Login success / execution |
| Post-Compromise | Persistence, lateral movement |
| Objective | Data theft, ransomware, impact |

Later stage = higher severity.

---

## 🚦 Severity Classification Model

### 🟢 LOW Severity

**Definition**
- Likely benign or failed attempt
- No confirmed compromise
- Minimal impact

**Typical Indicators**
- Failed login attempts
- Blocked phishing email
- Blocked malware download
- Scanning activity

**Action**
- Close with documentation
- Tune detection if noisy
- No escalation

---

### 🟡 MEDIUM Severity

**Definition**
- Suspicious activity
- Partial indicators
- No confirmed compromise

**Typical Indicators**
- User clicked phishing link (no login)
- Anomalous login with normal behavior
- Script execution blocked by EDR
- Suspicious PowerShell command (no follow-up)

**Action**
- Deeper investigation
- Monitor closely
- Possibly notify user

---

### 🔴 HIGH Severity

**Definition**
- Confirmed malicious activity
- Limited scope
- No irreversible impact yet

**Typical Indicators**
- Successful credential use
- Malware execution confirmed
- Persistence attempt
- Lateral movement attempt

**Action**
- Escalate to IR
- Containment actions
- Credential reset / host isolation

---

### 🚨 CRITICAL Severity

**Definition**
- Confirmed compromise
- High impact or broad scope
- Business risk present

**Typical Indicators**
- Domain admin compromise
- Active C2 communication
- Data exfiltration
- Ransomware activity
- Cloud tenant compromise

**Action**
- Incident response activation
- Management notification
- Eviction process
- Full scope assessment

---

## 🧠 Severity Decision Table (Quick Use)

| Confidence | Impact | Scope | Stage | Result |
|---------|--------|-------|-------|-------|
| Low | Low | Single | Attempt | LOW |
| Medium | Medium | Single | Attempt | MEDIUM |
| High | Medium | Limited | Initial Access | HIGH |
| High | High | Broad | Post-Compromise | CRITICAL |
| Very High | Critical | Enterprise | Objective | CRITICAL |

---

## 🔍 Common Misclassification Mistakes

❌ Trusting tool severity blindly  
❌ Escalating everything to Critical  
❌ Ignoring scope  
❌ Ignoring business context  
❌ Confusing detection quality with impact  

---

## 🧪 Practical Examples

### Example 1
- Alert: Phishing email blocked
- Confidence: High
- Impact: Low
- Scope: Single
- Stage: Attempt

➡️ **Severity: LOW**

---

### Example 2
- Alert: User logged in from new country
- Confidence: Medium
- Impact: Medium
- Scope: Single
- Stage: Initial Access

➡️ **Severity: MEDIUM**

---

### Example 3
- Alert: Admin account used on multiple servers
- Confidence: High
- Impact: High
- Scope: Broad
- Stage: Post-Compromise

➡️ **Severity: CRITICAL**

---

## 🧠 Analyst Rule of Thumb

> If you are unsure between two severities —  
> choose the **lower**, then justify escalation with evidence.

Severity inflation destroys SOC effectiveness.

---

## 🏁 Final Takeaway

Effective alert classification is:
- Structured
- Repeatable
- Defensible
- Context-driven

This methodology turns alert handling from:
> Chaos → Control  
> Noise → Signal  
> Reaction → Judgment  

---
