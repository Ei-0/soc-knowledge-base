# 🕵️ Windows Forensics Artifacts

## 📌 Overview
**Forensic artifacts** are traces left behind by system activity.  
In Windows environments, these artifacts allow investigators to:
- Reconstruct attack timelines
- Identify attacker actions
- Validate alerts
- Support incident response and legal cases

From a **SOC & DFIR perspective**, artifacts are the evidence.

---

## 🧱 What Are Windows Forensics Artifacts?
Artifacts come from multiple sources:
- File system
- Registry
- Event logs
- Memory
- User activity
- Network traces

Each artifact answers a specific investigative question.

---

## 🗂️ Key Categories of Windows Artifacts

### 🔹 1. File System Artifacts
Provide evidence of file activity:
- File creation, modification, deletion
- Executable locations
- Timestamps (MAC times)

🔍 **SOC View**:
- Executables in user-writable directories are suspicious
- Timestamp anomalies may indicate anti-forensics

---

### 🔹 2. Registry Artifacts
Registry reveals:
- Persistence mechanisms
- Program execution history
- User activity

Common artifact areas:
- Autorun keys
- Recently executed programs
- Service configurations

🔍 **SOC View**:
- Persistence often lives here
- Registry changes help identify attacker intent

---

### 🔹 3. Event Log Artifacts
Event logs capture:
- Authentication events
- Process execution
- Service creation
- Security policy changes

🔍 **SOC View**:
- Core data source for timeline reconstruction
- Correlation across logs is critical

---

### 🔹 4. Process & Execution Artifacts
Reveal:
- What ran
- How it was executed
- Under which user context

Sources include:
- Process creation logs
- Command-line history
- Prefetch data

🔍 **SOC View**:
- Prefetch helps confirm execution
- Command-line artifacts reveal intent

---

### 🔹 5. User Activity Artifacts
Show user interaction:
- Recently opened files
- Program execution history
- Login sessions

🔍 **SOC View**:
- Helps distinguish user action vs malware automation

---

### 🔹 6. Memory Artifacts
Memory can contain:
- Running malware
- Decrypted payloads
- Credentials
- Network connections

🔍 **SOC View**:
- Critical for fileless malware detection
- Often volatile but extremely valuable

---

## ⏱️ Timeline Reconstruction
SOC and DFIR teams build timelines using:
- File timestamps
- Event logs
- Process execution order
- Authentication events

Timelines reveal:
- Initial access point
- Attack progression
- Persistence creation
- Impact stage

---

## 🚨 Anti-Forensics Techniques
Attackers may try to:
- Clear event logs
- Modify timestamps
- Delete artifacts
- Disable logging

🔍 **SOC View**:
- Anti-forensics itself is a strong indicator of compromise

---

## 📊 High-Value Artifacts for SOC Analysts
SOC teams should prioritize:
- Process creation events
- Authentication logs
- Registry persistence keys
- Service and task creation
- Evidence of log tampering

These artifacts appear in most investigations.

---

## 🧩 Mapping to MITRE ATT&CK
Forensic artifacts support detection across:
- Execution
- Persistence
- Privilege Escalation
- Credential Access
- Defense Evasion
- Lateral Movement

Artifacts help confirm ATT&CK hypotheses.

---

## 🧪 Real-World Investigation Example
1. Alert triggers on suspicious PowerShell
2. Process logs confirm execution
3. Registry shows autorun persistence
4. Event logs reveal admin privilege assignment
5. Timeline confirms full compromise

Artifacts turn alerts into evidence.

---

## 🧠 SOC Analyst Mindset
Always ask:
- What evidence proves this happened?
- Can I recreate the timeline?
- Is persistence still active?
- Did the attacker try to hide?

Good analysts think like investigators.

---

