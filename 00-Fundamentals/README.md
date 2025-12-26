# 00 - Fundamentals

This section establishes the foundational cybersecurity concepts required
for anyone pursuing a role in a Security Operations Center (SOC).

Before analyzing alerts, logs, or incidents, a SOC Analyst must understand
core security principles, threat concepts, and attacker behavior.
These fundamentals form the mindset required for effective detection
and incident response.

---

## 🎯 Objectives of This Section
By completing this section, you will be able to:
- Understand core cybersecurity concepts
- Identify different types of threats and attacks
- Think like both a defender and an attacker
- Understand how incidents are classified and prioritized
- Build a strong foundation for SOC analysis

---

## 📚 Topics Covered

- Cybersecurity Fundamentals
- Confidentiality, Integrity, and Availability (CIA Triad)
- Types of Threats and Threat Actors
- Attack Lifecycle & Kill Chain Concepts
- Pyramid of Pain
- Incident Severity & Classification
- Basic Risk and Impact Concepts
- SOC Analyst Roles and Responsibilities

Each topic is written with a **SOC-first mindset**, focusing on how concepts
apply during real-world investigations rather than academic theory.

---

## 🧠 Why Fundamentals Matter in SOC
SOC Analysts are not just monitoring tools — they are making decisions.

Without strong fundamentals:
- Alerts may be misclassified
- Incidents may be underestimated
- Attacks may go undetected longer

> **Strong fundamentals lead to faster, more accurate investigations.**

---

## 🔐 Core Security Principles (CIA Triad)
<img width="750" height="419" alt="image" src="https://github.com/user-attachments/assets/e82e72b4-7d28-4800-96ed-9aa95843aa1c" />

- **Confidentiality:** Prevent unauthorized access to information
- **Integrity:** Ensure data accuracy and trust
- **Availability:** Ensure systems and services remain accessible

SOC Analysts must evaluate incidents based on which CIA principles
are impacted.

---

## ⚔️ Attacker vs Defender Mindset
This section introduces how attackers:
- Reconnaissance targets
- Exploit weaknesses
- Maintain persistence
- Evade detection

Understanding attacker behavior allows SOC Analysts to anticipate
and detect malicious activity earlier.

---

## 🧪 SOC Thinking Scenarios (Fundamentals)

This section includes high-level SOC scenarios focused on analyst thinking,
incident classification, severity assessment, and decision-making.

These scenarios intentionally avoid deep technical analysis and instead
train the mindset required for effective SOC operations.

---
<img width="960" height="720" alt="image" src="https://github.com/user-attachments/assets/f2e490e1-d9aa-4dc3-a14c-f33f085a1732" />

### 🟢 Scenario 01 — Multiple Failed Login Attempts

**Alert:**  
Multiple failed login attempts detected for a user account.

**SOC Questions:**
- Is this user error or brute-force activity?
- Is the account privileged?
- Are attempts coming from one IP or multiple IPs?

**Initial Classification:**
- Event Type: Authentication Event
- Severity: Low → Medium
- CIA Impact: Confidentiality

**SOC Decision:**
- Monitor for escalation
- No immediate containment required

---

### 🟡 Scenario 02 — Malware Detected and Quarantined

**Alert:**  
Endpoint protection detected malware and successfully quarantined it.

**SOC Questions:**
- Did the malware execute?
- Was there any outbound communication?
- Could other systems be affected?

**Initial Classification:**
- Event Type: Malware
- Severity: Medium
- CIA Impact: Integrity

**SOC Decision:**
- Validate containment
- Review related alerts
- Close if no additional indicators are found

---

### 🔴 Scenario 03 — Suspicious Outbound Network Connection

**Alert:**  
An internal host attempted to connect to an unknown external IP address.

**SOC Questions:**
- Is the destination trusted or known?
- Is the traffic encrypted?
- Is this a one-time event or repeated behavior?

**Initial Classification:**
- Event Type: Suspicious Network Activity
- Severity: High
- CIA Impact: Confidentiality

**SOC Decision:**
- Escalate to incident investigation
- Analyze endpoint and network context

---

### 🟣 Scenario 04 — Privileged Account Login Outside Business Hours

**Alert:**  
A privileged account logged in at 03:00 AM.

**SOC Questions:**
- Is this activity expected or approved?
- From which location did the login occur?
- Is multi-factor authentication enabled?

**Initial Classification:**
- Event Type: Account Misuse
- Severity: High
- CIA Impact: Confidentiality & Integrity

**SOC Decision:**
- Immediate investigation
- Validate user activity
- Monitor for post-login actions

---

## 🧠 Key Takeaways for SOC Analysts
- Not every alert is an incident
- Severity depends on context, not alert volume
- Classification guides response
- Strong fundamentals lead to better technical investigations

> **Before analyzing logs, a SOC Analyst must analyze the situation.**


## 🧪 Mini SOC Thinking Example

**Alert:** Multiple failed login attempts  
**SOC Questions:**
- Is this brute force or user error?
- Is the account privileged?
- What is the potential impact?
- Does this affect availability or confidentiality?

Fundamentals guide these decisions.
<img width="1418" height="1372" alt="image" src="https://github.com/user-attachments/assets/b77b28bd-69ea-4f06-b309-7377c1ea1bb7" />

---

## 🚀 How This Section Fits in the Project
This section prepares you for:
- **01 - Networking:** Understanding how attacks move
- **02 - Protocols:** Understanding how attacks communicate
- **03 - Operating Systems:** Understanding host behavior
- **04 - Command Line:** Investigation and triage
- **05 - Security Tools:** Detection and response

---

## ✅ Outcome
After completing this section, you will:
- Think like a SOC Analyst
- Understand the language of security
- Be prepared for deeper technical sections

> **Fundamentals are not optional — they are the difference between
> reacting to alerts and understanding incidents.**

---
