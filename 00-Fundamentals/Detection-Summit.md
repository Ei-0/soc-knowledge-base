# 🏔️ Detection Summit — Measuring SOC Detection Coverage

The **Detection Summit** represents the highest level of SOC maturity:
the ability to **understand, measure, and improve detection coverage**
across the attacker lifecycle.

SOC teams do not fail because they lack tools —
they fail because they **do not know what they are blind to**.

Detection Summit thinking answers:
- What do we detect well?
- What do we detect late?
- What do we not detect at all?

---

## 🎯 Why Detection Coverage Matters in SOC

Most SOCs:
- Have many alerts
- But limited visibility into **coverage quality**

Detection coverage focuses on:
- **Where** detections exist
- **When** detections trigger
- **How reliable** they are

Good coverage = early disruption  
Poor coverage = late-stage firefighting

---

## 🔗 Detection Summit ↔ Unified Kill Chain

Detection maturity increases the earlier you detect in the UKC.

| UKC Phase | Detection Value | SOC Impact |
|---------|----------------|------------|
| Reconnaissance | Very High | Prevents intrusion |
| Initial Foothold | High | Stops compromise |
| Network Propagation | Medium | Limits spread |
| Actions on Objectives | Low | Damage already done |

SOC maturity is defined by **how early** in the UKC you can detect.

---

## 🔍 Detection Summit ↔ MITRE ATT&CK

MITRE ATT&CK provides:
- **What attackers do**

Detection Summit measures:
- **What you can detect**

This creates three critical questions:
1. Which ATT&CK tactics are covered?
2. Which are partially covered?
3. Which are not covered at all?

---

## 🧩 Detection Coverage Levels (SOC Perspective)

### 🟥 Level 1 — IOC-Based Detection
- Hashes, IPs, domains
- High false negatives
- Easy to evade

### 🟧 Level 2 — Technique-Based Detection
- ATT&CK technique patterns
- Better resilience
- Requires tuning

### 🟨 Level 3 — Behavior-Based Detection
- Anomaly and behavior analytics
- Low attacker dependency
- Higher SOC maturity

### 🟩 Level 4 — Campaign-Level Detection (Summit)
- Cross-stage correlation
- UKC-aware detections
- Predictive response

---

## 🧠 What Reaching the Detection Summit Looks Like

A SOC at the Detection Summit:
- Maps detections to ATT&CK tactics
- Maps alerts to UKC stages
- Knows exactly where gaps exist
- Detects attackers **before objectives**
- Improves detections continuously

Alerts are not isolated —
they are **signals in a campaign**.

---

## 🧪 Applying Detection Summit to the Incident Case

From the phishing campaign case:

| Stage | Detection | Coverage Quality |
|----|---------|----------------|
| Reconnaissance | ❌ None | Blind spot |
| Delivery | ✅ Email alert | Partial |
| Credential Abuse | ✅ Auth anomaly | Good |
| Lateral Expansion | ⚠️ Delayed | Weak |
| Exfiltration | ✅ Detected | Late |

Detection Summit analysis reveals:
- Over-reliance on late-stage alerts
- Weak early-phase visibility
- Opportunity for proactive detections

---

## 📈 How SOC Teams Improve Detection Coverage

- Map all detections to ATT&CK
- Align detections with UKC stages
- Identify early-stage gaps
- Build behavior-based rules
- Measure detection latency
- Review coverage quarterly

Detection improvement is a **process**, not a project.

---
<img width="1590" height="889" alt="image" src="https://github.com/user-attachments/assets/40a9e399-a72c-483d-86de-b003976fe599" />
<img width="1600" height="871" alt="image" src="https://github.com/user-attachments/assets/830f690c-b013-43f0-9e7b-c69469c0b62b" />
<img width="827" height="537" alt="image" src="https://github.com/user-attachments/assets/cb77a35f-bcda-4a70-bb41-e3a1744a211f" />

## 🏁 Final SOC Insight

Tools do not define SOC maturity.

**Visibility + Context + Coverage** do.

Reaching the Detection Summit means:
- Fewer surprises
- Earlier detections
- Stronger defense
- Smarter analysts
