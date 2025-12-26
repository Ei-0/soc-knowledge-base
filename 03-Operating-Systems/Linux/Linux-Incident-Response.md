# 🚑 Linux Incident Response (SOC & DFIR Playbook)

## 📌 Overview
This document provides a **practical incident response playbook** for Linux systems.

From a SOC and DFIR perspective, Linux Incident Response focuses on:
- Fast containment
- Evidence preservation
- Accurate scoping
- Safe eradication
- Preventing reinfection

The first minutes matter more than perfect analysis.

---

## 🎯 Incident Response Goals
When responding to a Linux incident, the goals are:
1. Protect the environment
2. Preserve evidence
3. Stop attacker activity
4. Understand what happened
5. Prevent recurrence

Do **not** rush to “clean” before understanding.

---

## 🕒 Phase 1: Identification

### Key Questions
- Is this system compromised?
- What triggered the alert?
- Is this part of a wider incident?

### Initial Indicators
- Suspicious SSH logins
- Unexpected sudo usage
- Unknown processes
- New cron jobs or services
- Outbound connections from shells

### Actions
- Validate alerts
- Check auth logs
- Identify affected users
- Determine potential attacker access

---

## 🛑 Phase 2: Containment

### Immediate Containment Options
- Isolate host from the network
- Disable outbound access
- Restrict SSH access
- Disable compromised accounts

### SOC Notes
- Prefer network isolation over shutdown
- Avoid rebooting unless required
- Keep the system running for live evidence

Containment stops damage but preserves visibility.

---

## 🧾 Phase 3: Evidence Preservation

### What to Preserve
- Authentication logs
- Process lists
- Network connections
- Persistence mechanisms
- Memory (if possible)

### Key Artifacts
- `/var/log/auth.log` or `/var/log/secure`
- Running processes (`ps`)
- Network state
- Cron jobs
- systemd services
- SSH keys

### SOC Notes
- Copy evidence to secure storage
- Record timestamps
- Maintain chain of custody if required

---

## 🔍 Phase 4: Investigation & Analysis

### Investigation Focus
- Initial access vector
- Commands executed
- Privilege escalation path
- Persistence mechanisms
- Lateral movement attempts
- Anti-forensics activity

### Analysis Sources
- Logs
- Process telemetry
- File system changes
- Network activity
- Configuration modifications

Build a **timeline** of attacker actions.

---

## 🧹 Phase 5: Eradication

### Eradication Actions
- Remove persistence (cron, services, keys)
- Remove malicious users
- Reset compromised credentials
- Patch vulnerabilities
- Harden SSH and sudo configs

### SOC Notes
- Verify persistence removal
- Check for multiple backdoors
- Do not assume one mechanism only

---

## 🔄 Phase 6: Recovery

### Recovery Actions
- Restore services safely
- Re-enable network access
- Monitor closely for recurrence
- Validate system integrity

### SOC Notes
- Increased monitoring post-incident
- Look for attacker re-entry attempts
- Validate backups before restoration

---

## 🧠 Phase 7: Lessons Learned

### Key Questions
- How did the attacker get in?
- What failed?
- What detection gaps exist?
- What controls need improvement?

### Improvements
- SSH hardening
- Better logging
- Network segmentation
- Credential hygiene
- Monitoring expansion

Incidents are learning opportunities.

---

## 🚨 Common Linux IR Mistakes
Avoid:
- Immediate reboot
- Deleting files before analysis
- Rotating logs prematurely
- Assuming single-host compromise
- Ignoring outbound traffic

---

## 🧩 MITRE ATT&CK Usage in IR
MITRE helps:
- Classify attacker behavior
- Communicate findings
- Map controls to gaps
- Improve detections

IR uses MITRE to explain **what happened**, not just how.

---

## 🧪 Example Linux Incident Response Flow
1. Alert: Suspicious SSH login
2. Containment: Network isolation
3. Evidence: Logs + process capture
4. Investigation: Cron persistence found
5. Eradication: Remove cron + SSH keys
6. Recovery: Restore access
7. Lessons: Disable password SSH

---

## 🧠 SOC Analyst Mindset
Always remember:
- Speed with discipline
- Evidence before cleanup
- Scope before fix
- Persistence before trust

Good incident response is calm, methodical, and documented.

---

