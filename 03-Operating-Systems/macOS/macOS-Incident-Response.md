# macOS Incident Response — Playbooks, Actions & SOC Reality (DFIR)


---

## Overview

Incident response on macOS is **time‑sensitive and permission‑dependent**.

Due to:
- Short log retention  
- User‑consent controls  
- Limited kernel visibility  

SOC teams must act **quickly and methodically** to preserve evidence.

---

## macOS IR Core Principles

1. Time is evidence  
2. Assume partial visibility  
3. User context matters  
4. Persistence comes first  
5. Logs expire quickly  

macOS IR is about **prioritization**, not perfection.

---

## Incident Response Phases (macOS)

### 1. Identification

Common detection sources:
- EDR alerts  
- User reports  
- Network anomalies  
- Suspicious permission grants  

Key questions:
- Which user?  
- What permissions were granted?  
- Is persistence present?  

---

### 2. Containment

Immediate actions:
- Isolate endpoint from network  
- Disable remote access (SSH, Screen Sharing)  
- Preserve running state  

Avoid:
- Rebooting (destroys volatile evidence)  
- Killing processes blindly  

---

### 3. Evidence Collection (Live Response)

Priority order:
1. Unified Logs  
2. Running processes  
3. Persistence mechanisms  
4. User permissions (TCC)  
5. Network connections  

Examples:

```bash
log collect
ps aux
launchctl list
```

---

### 4. Persistence Identification

Enumerate:
- LaunchAgents  
- LaunchDaemons  
- Login Items  
- Configuration Profiles  
- Shell init files  

**Remove persistence before killing malware.**

---

### 5. Eradication

Steps:
- Remove persistence artifacts  
- Delete malicious binaries or scripts  
- Revoke permissions (TCC)  
- Remove malicious profiles  
- Rotate credentials  

**SOC Note:**  
Signed malware must still be removed.

---

### 6. Recovery

Actions:
- Restore system settings  
- Re‑enable security controls  
- Monitor for re‑infection  
- Validate clean state  

In high‑risk cases:
- Reimage device  

---

### 7. Lessons Learned

Post‑incident review:
- Initial access vector  
- Detection gaps  
- Response delays  
- User behavior factors  

Improve:
- Detection rules  
- User awareness  
- Response playbooks  

---

## Common macOS IR Mistakes

- Waiting too long to collect logs  
- Rebooting early  
- Ignoring user permissions  
- Focusing only on binaries  
- Assuming Windows‑like visibility  

---

## Tooling Considerations

macOS IR tools must:
- Have Full Disk Access  
- Be approved by users  
- Respect SIP limitations  

Examples:
- EDR live response  
- Apple‑provided utilities  
- Custom scripts  

---

## Executive Devices (Special Case)

Executives are:
- High‑value targets  
- Low technical users  
- Often have admin rights  

IR Strategy:
- Prioritize speed  
- Minimize user disruption  
- Assume credential compromise  

---

## Documentation & Reporting

Document:
- Timeline  
- Permissions granted  
- Persistence artifacts  
- User actions  
- Logs collected  

macOS incidents require **strong narrative context**.

---

## Key Takeaways

- macOS IR is permission‑driven  
- Logs are volatile  
- Persistence is the anchor  
- User behavior matters  
- Speed beats depth  

---
