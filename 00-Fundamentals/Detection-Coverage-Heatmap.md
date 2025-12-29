# 🌡️ Detection Coverage Heatmap (UKC × MITRE)

A **Coverage Heatmap** visualizes detection strength across
the **Unified Kill Chain stages** and **MITRE ATT&CK tactics**.

It answers one critical SOC question:
> “Where are we blind, weak, or strong?”
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/25d0ac09-dd1f-4d8d-98d7-6980268d61f7" />

---

## 🧩 Example Coverage Heatmap (Conceptual)

| UKC Phase | MITRE Tactic | Coverage Level | Notes |
|---------|--------------|----------------|------|
| Reconnaissance | Reconnaissance | ❌ None | External visibility gap |
| Initial Foothold | Initial Access | 🟨 Partial | Email-only detection |
| Persistence | Persistence | 🟩 Good | Endpoint telemetry |
| Privilege Escalation | Privilege Escalation | 🟨 Partial | Limited alerts |
| Lateral Movement | Lateral Movement | 🟥 Weak | High detection latency |
| Command & Control | C2 | 🟩 Good | Network analytics |
| Exfiltration | Exfiltration | 🟥 Weak | Detected too late |
| Impact | Impact | 🟩 Good | Ransomware signals |

Legend:
- 🟩 Good Coverage
- 🟨 Partial Coverage
- 🟥 Weak Coverage
- ❌ No Coverage

---

## 🧠 How SOC Teams Use the Heatmap

- Prioritize detection engineering
- Identify early-stage blind spots
- Reduce over-investment in late-stage alerts
- Communicate risk clearly to management

Heatmaps turn **gut feeling** into **measurable visibility**.

---

## 📊 SOC KPIs Built on Unified Kill Chain

Traditional SOC metrics focus on volume.
UKC-based KPIs focus on **effectiveness**.

---

## 🔑 Core UKC-Based SOC KPIs

### 1️⃣ Detection Stage Index (DSI)

**What it measures:**  
Average UKC stage where incidents are first detected.

- Lower stage = better SOC maturity
- Higher stage = reactive SOC

---

### 2️⃣ Detection Latency per UKC Phase

**What it measures:**  
Time between attacker action and detection at each UKC stage.

Example:
- Recon → Detected in 2 hours
- Lateral Movement → Detected in 30 minutes

---

### 3️⃣ Early-Stage Detection Ratio

**What it measures:**  
Percentage of incidents detected before:
- Privilege Escalation
- Lateral Movement

Early detection = lower business impact.

---

### 4️⃣ Coverage Gap Index

**What it measures:**  
Number of UKC stages with:
- Weak or no detection

Used to guide detection backlog.

---

### 5️⃣ Campaign Visibility Score

**What it measures:**  
How many incidents were detected as **campaigns**, not single alerts.

High score = mature correlation capability.

---

## 🧠 Why UKC KPIs Matter

They shift SOC conversations from:
> “How many alerts did we close?”

To:
> “How early did we stop the attacker?”

---

## 🗺️ Roadmap to the Detection Summit (SOC Maturity Path)
<img width="1024" height="535" alt="image" src="https://github.com/user-attachments/assets/8ba8728e-d661-49d7-98bb-258567084231" />

Reaching the Detection Summit is a **journey**, not a tool purchase.

---

## 🟥 Stage 1 — Reactive SOC

**Characteristics**
- IOC-heavy detections
- Alert-driven response
- Minimal context

**Focus**
- Stabilize logging
- Reduce noise
- Build basic ATT&CK mapping

---

## 🟧 Stage 2 — Technique-Aware SOC

**Characteristics**
- ATT&CK-based detections
- Some correlation
- Improved triage

**Focus**
- Technique-level rules
- Detection tuning
- False positive reduction

---

## 🟨 Stage 3 — Behavior-Based SOC

**Characteristics**
- Behavioral analytics
- Cross-data correlation
- Reduced attacker dependency

**Focus**
- UKC stage awareness
- Detection latency reduction
- Early-stage visibility

---

## 🟩 Stage 4 — Detection Summit (Campaign-Aware SOC)

**Characteristics**
- Campaign-level detection
- UKC + ATT&CK correlation
- Predictive response

**Capabilities**
- Early disruption
- Clear detection gaps
- Continuous improvement loop

This is where SOC becomes **proactive**, not reactive.

---

## 🔁 Continuous Improvement Loop

1. Measure coverage (Heatmap)
2. Track KPIs
3. Identify gaps
4. Build detections
5. Validate with incidents
6. Repeat

SOC maturity is **measured**, not claimed.

---

## 🏁 Final Strategic Insight

A mature SOC:
- Knows **what attackers do**
- Knows **where it can see**
- Knows **where it is blind**
- Improves deliberately

Reaching the Detection Summit is not about having
more alerts —  
it is about having **the right detections at the right time**.
