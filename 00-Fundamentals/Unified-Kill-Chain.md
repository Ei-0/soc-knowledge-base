# 🧬 Unified Kill Chain (UKC) — The Attacker Campaign Model
<img width="1200" height="775" alt="image" src="https://github.com/user-attachments/assets/08c09785-5fe9-4069-95e0-a6ac8b03ebcc" />

## 🎯 Purpose

This document provides a **complete SOC-oriented view** of the
**Unified Kill Chain (UKC)** by combining:

- Correct UKC model explanation
- Mapping to **MITRE ATT&CK tactics**
- Detection opportunities at each stage
- A full incident case analyzed through UKC

The goal is to move SOC analysis from **isolated alerts**
to **attacker campaign understanding**.

---

## 🧬 Unified Kill Chain (UKC) — Correct Overview

The **Unified Kill Chain (UKC)** models **real-world adversary campaigns**
as continuous, non-linear operations.

Key characteristics:
- Attacker-centric
- Covers pre- and post-compromise activity
- Focuses on campaign progression
- Stages can overlap or repeat

UKC explains **how attackers think and operate**, not just what tools they use.

---

## 🔗 UKC Macro Phases

UKC is grouped into three macro phases:
<img width="1200" height="334" alt="image" src="https://github.com/user-attachments/assets/50e9c97c-188c-496f-ac3d-c6449b7cf711" />

1. **Initial Foothold**
2. **Network Propagation**
3. **Action on Objectives**

Each contains multiple operational stages.

---

## 🧩 UKC ↔ MITRE ATT&CK Mapping + Detection Opportunities

### 🟦 Phase 1 — Initial Foothold

| UKC Stage | MITRE ATT&CK Tactics | Detection Opportunities |
|---------|---------------------|-------------------------|
| Reconnaissance | Reconnaissance | External scanning logs, DNS enumeration, OSINT leakage |
| Resource Development | Resource Development | Newly registered domains, phishing infra reuse |
| Delivery | Initial Access | Email telemetry, web proxy logs |
| Social Engineering | Initial Access | User behavior anomalies, phishing reports |
| Exploitation | Execution | Exploit detection, abnormal process creation |
| Persistence | Persistence | Startup items, scheduled tasks |
| Defense Evasion | Defense Evasion | Log tampering, disabled security tools |

---

### 🟧 Phase 2 — Network Propagation

| UKC Stage | MITRE ATT&CK Tactics | Detection Opportunities |
|---------|---------------------|-------------------------|
| Privilege Escalation | Privilege Escalation | Unexpected admin rights, token abuse |
| Credential Access | Credential Access | LSASS access, credential dumping tools |
| Lateral Movement | Lateral Movement | SMB/RDP anomalies, service creation |
| Discovery | Discovery | Enumeration commands, AD queries |
| Collection | Collection | Mass file access, staging directories |

---

### 🟥 Phase 3 — Action on Objectives

| UKC Stage | MITRE ATT&CK Tactics | Detection Opportunities |
|---------|---------------------|-------------------------|
| Command & Control | Command and Control | Beaconing patterns, suspicious outbound traffic |
| Exfiltration | Exfiltration | Large outbound transfers, unusual protocols |
| Impact | Impact | Encryption activity, service disruption |
| Obfuscation / Anti-Forensics | Defense Evasion | Log deletion, timestomping |
| Monetization | Impact | Ransom notes, crypto activity |
| Sustainment | Persistence | Re-established access after cleanup |

---

## 🧠 Why Detection Opportunities Matter

Detection is strongest when:
- Multiple UKC stages are correlated
- Early-phase activity is identified
- Analysts understand **what comes next**

Early detection = campaign disruption  
Late detection = damage control

---

## 🧪 Incident Case Study — Credential Phishing Campaign

### Scenario Overview

A SOC receives an alert for:
- Suspicious login from a new country
- Followed by mailbox rule creation

---

## 🔍 Incident Analysis Using Unified Kill Chain

### Phase 1 — Initial Foothold

- **Reconnaissance**
  - Attacker harvested employee emails from LinkedIn

- **Resource Development**
  - Lookalike domain registered 3 weeks earlier

- **Delivery**
  - Phishing email sent with fake MFA prompt

- **Social Engineering**
  - User approved push notification

- **Exploitation**
  - Valid credentials used successfully

**MITRE Tactics:** Initial Access  
**SOC Detection:** Email logs + authentication anomalies

---

### Phase 2 — Network Propagation

- **Credential Access**
  - OAuth token abuse detected

- **Discovery**
  - Attacker accessed directory information

- **Collection**
  - Email data staged in mailbox folders

**MITRE Tactics:** Credential Access, Discovery  
**SOC Detection:** Audit logs, mailbox rule alerts

---

### Phase 3 — Action on Objectives

- **Command & Control**
  - API-based access to mailbox

- **Exfiltration**
  - Email forwarding to external account

- **Sustainment**
  - MFA fatigue continued on other users

**MITRE Tactics:** Exfiltration, Persistence  
**SOC Detection:** API usage anomalies

---

## 🚨 SOC Response Decisions

- Account disabled
- Sessions revoked
- Phishing domain blocked
- IOC sweep across tenant
- User awareness follow-up

---

## 🧠 What UKC Revealed That Alerts Alone Did Not

- This was not a single alert
- This was an **ongoing campaign**
- Other users were likely targeted
- Detection gaps existed in early recon stages

UKC transformed:
> Alerts → Narrative  
> Logs → Campaign  
> Incident → Lessons Learned

---

## 🏁 Final Takeaway

Unified Kill Chain enables SOC teams to:
- Understand attacker intent
- Predict next steps
- Prioritize detection engineering
- Communicate incidents clearly

SOC maturity is not measured by tools —  
but by **how well attackers are understood and disrupted**.
