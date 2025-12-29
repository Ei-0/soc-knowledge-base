# 🚪 Adversary Eviction — Removing the Attacker for Good

**Eviction** is the disciplined process of **fully removing an attacker**
from the environment — not just stopping alerts or closing incidents.

Detection tells you *an attacker exists*.  
Eviction ensures the attacker **cannot return**.

Many SOCs detect intrusions.
Few SOCs **successfully evict adversaries**.

---

## 🎯 What Eviction Really Means

Eviction is NOT:
- Blocking one IP
- Resetting one password
- Killing one process
- Closing one ticket

Eviction IS:
- Removing access
- Removing persistence
- Removing stolen credentials
- Removing attacker advantage
- Verifying the attacker is gone

---

## 🧠 Why Eviction Fails in Immature SOCs

Common failure patterns:
- Focusing only on the detected host
- Ignoring lateral movement
- Resetting credentials before understanding scope
- Containing before visibility is complete
- Treating incidents as isolated events

Result:
> Attacker returns — often stronger and stealthier.

---

## 🔗 Eviction in the Unified Kill Chain Context

Eviction targets **multiple UKC stages at once**.

| UKC Phase | Eviction Objective |
|---------|-------------------|
| Persistence | Remove all footholds |
| Credential Access | Invalidate stolen secrets |
| Lateral Movement | Cut expansion paths |
| Command & Control | Break attacker control |
| Sustainment | Prevent re-entry |

Eviction is a **campaign-level action**, not a host-level fix.

---

## 🧩 Eviction Preconditions (Critical)

Before eviction, SOC must confirm:

- Full scope visibility
- All affected identities identified
- All persistence mechanisms enumerated
- All C2 channels understood
- Business impact assessed

Eviction without visibility = **forced retreat without reconnaissance**.

---

## 🔄 The Eviction Process (SOC-Oriented)

### 1️⃣ Scope Confirmation

- Identify all compromised users
- Identify all compromised systems
- Identify cloud, identity, and on-prem touchpoints

**UKC stages addressed:** Discovery, Collection

---

### 2️⃣ Persistence Eradication

- Remove scheduled tasks
- Remove startup items
- Remove OAuth grants
- Remove backdoors

**UKC stages addressed:** Persistence, Sustainment

---

### 3️⃣ Credential Invalidation

- Reset affected accounts
- Rotate API keys
- Revoke tokens
- Reset service accounts

**UKC stages addressed:** Credential Access

---

### 4️⃣ Command & Control Disruption

- Block domains/IPs
- Disable compromised services
- Kill beaconing paths

**UKC stages addressed:** Command & Control

---

### 5️⃣ Controlled Containment

- Isolate hosts (if needed)
- Apply fixes in waves
- Monitor attacker reaction

**Key principle:** Do not tip off attacker too early.

---

### 6️⃣ Verification & Monitoring

- Look for re-compromise attempts
- Monitor authentication failures
- Watch for persistence recreation
- Validate detection coverage

Eviction is not complete without **confirmation**.

---

## 🧠 Eviction vs Containment vs Remediation

| Term | Purpose | Risk |
|----|-------|------|
| Containment | Stop immediate harm | Attacker may persist |
| Remediation | Fix vulnerabilities | Miss hidden access |
| Eviction | Remove attacker entirely | Requires discipline |

Eviction includes containment and remediation — but goes further.

---

## 📊 Eviction Success Metrics (SOC KPIs)

- Re-compromise rate (should approach zero)
- Time to full eviction
- Number of missed persistence mechanisms
- Detection of eviction-triggered activity
- Attacker dwell time reduction

These metrics reflect **true SOC effectiveness**.

---

## 🧪 Applying Eviction to the Incident Case

From the phishing campaign:

- Resetting user password ❌ insufficient
- Revoking OAuth tokens ✅
- Removing mailbox rules ✅
- Checking other users for MFA fatigue ✅
- Monitoring API abuse post-reset ✅

Eviction required **identity-wide action**, not a single fix.

---

## 🏁 Final Eviction Insight

Detection finds attackers.  
Response slows them.  
**Eviction defeats them.**

A mature SOC is defined not by:
- How fast it closes tickets

But by:
- How completely it removes adversaries
- How confidently it prevents return

Eviction is the final proof of SOC maturity.
<img width="621" height="361" alt="image" src="https://github.com/user-attachments/assets/c99800d2-bb90-4039-a945-68fb01401b5e" />
<img width="1997" height="969" alt="image" src="https://github.com/user-attachments/assets/a18ef191-5aa5-408f-b639-c5357eb61dd9" />
---

## ✅ Adversary Eviction — Practical SOC Checklist

This checklist ensures **complete adversary removal**, not partial cleanup.
It is designed for **SOC, IR, and Blue Team execution**.

Use this checklist **before, during, and after eviction**.

---

## 🧾 Pre-Eviction Checklist (Visibility First)

☐ Incident scope confirmed  
☐ All affected users identified  
☐ All affected hosts identified  
☐ Cloud / Identity / SaaS impact reviewed  
☐ Persistence mechanisms enumerated  
☐ Credential exposure assessed  
☐ Command & Control paths identified  
☐ Business impact approved  

🚫 Do NOT evict if visibility is incomplete.

---

## 🧹 Eviction Execution Checklist

### 🔐 Identity & Access
☐ Reset compromised user credentials  
☐ Revoke all active sessions  
☐ Revoke OAuth / API tokens  
☐ Rotate service account credentials  
☐ Enforce MFA reset if applicable  

---

### 🖥️ Endpoint & Infrastructure
☐ Remove scheduled tasks / cron jobs  
☐ Remove startup persistence  
☐ Remove malicious services  
☐ Validate EDR clean state  
☐ Isolate hosts if required  

---

### 🌐 Network & C2
☐ Block malicious domains/IPs  
☐ Disable compromised VPN access  
☐ Review DNS / proxy logs for fallback C2  
☐ Validate outbound traffic normalization  

---

### ☁️ Cloud & SaaS
☐ Review mailbox rules / forwarding  
☐ Remove malicious OAuth apps  
☐ Audit admin activity  
☐ Validate audit logging coverage  

---

## 🔍 Post-Eviction Verification Checklist

☐ No re-authentication attempts observed  
☐ No persistence re-creation detected  
☐ No C2 traffic observed  
☐ Detection rules triggered during eviction (expected)  
☐ No new alerts tied to previous IOCs  

Eviction is **not complete** until verification passes.

---

## 🧠 Post-Eviction Threat Hunting

Eviction assumes **you may have missed something**.
Threat hunting validates that assumption.

---

## 🔎 Post-Eviction Threat Hunting Objectives

- Confirm attacker removal
- Detect dormant persistence
- Identify previously missed activity
- Validate detection improvements

---

## 🧪 Recommended Post-Eviction Hunts

### 1️⃣ Identity Abuse Hunt
- Authentication from unusual locations
- Legacy protocol usage
- Token reuse patterns

---

### 2️⃣ Persistence Re-Creation Hunt
- Reappearance of startup items
- Re-created scheduled tasks
- Registry or launch agent recreation

---

### 3️⃣ Lateral Movement Residue Hunt
- SMB / RDP anomalies
- Service creation attempts
- Failed authentication bursts

---

### 4️⃣ C2 Resurrection Hunt
- DNS beaconing
- Periodic outbound traffic
- Previously blocked infrastructure reuse

---

### 5️⃣ UKC Gap Validation Hunt
- Which UKC stages were **not detected**
- Which stages were detected **too late**

Hunting feeds detection engineering.

---

## 📊 Threat Hunting Output (What to Document)

- New findings
- Missed detection opportunities
- Detection latency issues
- False assumptions corrected
- Improvements implemented

Threat hunting closes the loop.

---

## 🧾 Executive Eviction Brief Template

This template communicates eviction clearly to **non-technical leadership**.

---

### 📌 Executive Eviction Summary

**Incident Type:**  
Credential Compromise / Phishing Campaign  

**Business Impact:**  
Low / Medium / High  

**Status:**  
Attacker Successfully Evicted  

---

### 🧠 What Happened (Plain Language)

An external threat actor gained access using compromised credentials.
The attacker attempted to maintain access and extract data.
Security teams detected the activity and removed all attacker access.

---

### 🚪 What “Evicted” Means

- All attacker access removed  
- All stolen credentials invalidated  
- All persistence mechanisms removed  
- Monitoring confirmed no return  

This was not a temporary fix.

---

### ⏱️ Timeline (High-Level)

- Initial Detection:  
- Scope Confirmation:  
- Eviction Executed:  
- Verification Completed:  

---

### 🛡️ Risk Assessment

- Likelihood of Return: **Low**
- Data Loss: **None / Limited / Confirmed**
- Residual Risk: **Acceptable**

---

### 📈 Improvements Implemented

- Detection gaps addressed
- Additional monitoring enabled
- User awareness actions taken

---

### 🏁 Executive Assurance

Based on current evidence and post-eviction monitoring,
there is **no indication of continued attacker presence**.

Security posture has been strengthened.

---

## 🔁 Eviction Lifecycle (SOC Perspective)

Detection → Context → Containment → **Eviction**  
→ Verification → Threat Hunting → Improvement  

SOC maturity is proven **after** the attacker is gone.

---

## 🏁 Final SOC Insight

Eviction without hunting is optimism.  
Hunting without eviction is exposure.  

A mature SOC does **both** — deliberately.
