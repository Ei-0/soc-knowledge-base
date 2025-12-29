# 🧪 Email Phishing Analysis — Analyst Workflow

This section describes a **structured, repeatable workflow**
for SOC analysts when analyzing suspected phishing emails.

The goal is to:
- Identify malicious indicators
- Assess risk accurately
- Take appropriate response actions
- Document findings clearly

---
<img width="417" height="417" alt="image" src="https://github.com/user-attachments/assets/55acf825-c712-45a2-985f-7a2ae55cbfae" />

## 🧩 Step 1: Intake & Preservation

Before analysis begins:

- Preserve the original email
- Avoid clicking links or opening attachments
- Save the full email including headers
- Assign a tracking ID or case number

Integrity of evidence is critical.

---

## 🔍 Step 2: Sender & Metadata Review

### Key checks:
- Display name vs actual email address
- Domain reputation
- Reply-To mismatch
- Return-Path anomalies

Red flags:
- Lookalike domains
- Free email services impersonating organizations
- Recently registered domains

---

## 🧠 Step 3: Header Analysis

Review headers to determine:
- Source IP address
- Mail server path (Received headers)
- Authentication results

### Focus fields:
- `Received`
- `Return-Path`
- `Message-ID`
- `X-Originating-IP`
- SPF / DKIM / DMARC results

Indicators of phishing:
- SPF Fail or SoftFail
- DKIM Fail
- DMARC Fail or None
- Inconsistent sending infrastructure

---

## 🔗 Step 4: URL Analysis

### Extraction:
- Extract all URLs from the message body
- Identify shortened or obfuscated URLs
- Decode URL redirects if present

### Analysis:
- Domain age and registration details
- HTTPS certificate validity
- Page visual similarity to known brands
- External connections triggered by page load

Never click links directly from the email.

---

## 📎 Step 5: Attachment Analysis

### Static Analysis:
- File type and extension
- Hash calculation (SHA256 preferred)
- Metadata inspection
- Digital signature validation

### Dynamic Analysis:
- Sandbox execution
- Process behavior
- Network connections
- File system and registry changes

Indicators include:
- Child process spawning
- External network communication
- Persistence attempts

---

## ⚖️ Step 6: Risk Assessment

Classify the email based on:

- Malicious indicators present
- User interaction (clicked, downloaded, executed)
- Potential impact

### Example classification:
- Low: Spam, no malicious content
- Medium: Phishing attempt, no compromise
- High: Credential harvesting or malware delivery
- Critical: Confirmed compromise or lateral risk

---

## 🧾 Step 7: Documentation

Document clearly:
- Indicators of Compromise (IOCs)
- Tools used
- Analysis steps
- Risk level
- Recommended actions

Clear documentation enables:
- Faster response
- Knowledge sharing
- Legal and compliance support

---

## 🛡️ Step 8: Response Actions

Based on classification:
- Block sender and domains
- Remove emails from mailboxes
- Reset affected credentials
- Notify users if required
- Update detection rules

Response should be **proportional and timely**.
<img width="2000" height="1114" alt="image" src="https://github.com/user-attachments/assets/24345e92-599e-4814-b953-edf8a822c1a1" />
<img width="530" height="398" alt="image" src="https://github.com/user-attachments/assets/951af660-06c9-4613-8f86-521cdc28b1f6" />

---

## 🧠 Analyst Best Practices

- Do not rely on a single indicator
- Avoid confirmation bias
- Validate assumptions
- Think in patterns, not single emails
- When unsure, escalate

---

## 🏁 Summary

Effective phishing analysis combines:
- Technical skill
- Structured methodology
- Clear judgment
- Strong documentation

Consistency in analysis is more important than speed.
