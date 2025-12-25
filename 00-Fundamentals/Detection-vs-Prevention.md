# Detection vs Prevention

Cybersecurity controls are commonly divided into **prevention** and **detection**.
SOC teams primarily operate on the **detection side**.

---

## 🛑 Prevention
Stops attacks before they happen.

Examples:
- Firewalls
- Antivirus
- MFA
- Patch management

Limitations:
- Not 100% effective
- Attackers bypass controls

---

## 🚨 Detection
Identifies attacks that bypass prevention.

Examples:
- SIEM alerts
- EDR detections
- Behavioral analytics
- Log correlation

Strengths:
- Assumes breach
- Focuses on visibility

---

## 🧠 SOC Mindset
> Prevention will fail — detection must succeed.

SOC analysts:
- Validate alerts
- Investigate behavior
- Respond to confirmed incidents

---

## 🔁 Detection & MITRE ATT&CK
Detection logic is often mapped to **:contentReference[oaicite:1]{index=1}** techniques to identify attacker behavior.

---

## 🔗 Practice Mapping
Applied in:
- Alert triage
- Detection engineering
- Incident response

<img width="1920" height="999" alt="image" src="https://github.com/user-attachments/assets/3b5a8107-18cc-488b-8074-0da25c06f3b3" />
