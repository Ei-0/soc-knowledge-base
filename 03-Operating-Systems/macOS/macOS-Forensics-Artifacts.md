# macOS Forensics Artifacts — Evidence Sources & Analysis (SOC / DFIR)


---

## Overview

macOS forensics focuses on **user activity, persistence artifacts, and volatile logs**.

Due to Apple security controls:
- Disk artifacts are protected  
- Logs are short‑lived  
- Memory access is restricted  

Successful macOS DFIR requires **speed, prioritization, and context**.

---

## Core Artifact Categories

macOS forensic artifacts fall into these groups:
- Process & execution artifacts  
- Persistence artifacts  
- User activity artifacts  
- Authentication & permission artifacts  
- Network‑related artifacts  
- Backup & snapshot artifacts  

---

## Process & Execution Artifacts

### Unified Logs (Primary Source)

Access via:

```bash
log show
log stream
```

Relevant data:
- Process execution  
- Parent‑child relationships  
- Permission usage  
- Errors and failures  

⚠️ **Logs rotate quickly — collect early.**

---

### Quarantine Events

Files downloaded from the internet include:

```
com.apple.quarantine
```

Artifacts:
- Extended attributes  
- Gatekeeper decisions  
- First execution events  

---

## Persistence Artifacts

### launchd Artifacts

Paths:

```
~/Library/LaunchAgents
/Library/LaunchAgents
/Library/LaunchDaemons
```

Artifacts:
- Plist creation time  
- ProgramArguments  
- RunAtLoad / KeepAlive  

---

### Login Items

Stored in:

```
~/Library/Application Support/com.apple.backgroundtaskmanagementagent
```

Indicators:
- Unexpected background items  
- Recently added entries  

---

### Configuration Profiles

Stored in:

```
/var/db/ConfigurationProfiles
```

Artifacts:
- Installed profiles  
- Payload contents  
- Install timestamps  

🚩 **Profiles are high‑impact persistence.**

---

## User Activity Artifacts

### User Home Directory

High‑value locations:

```
~/Downloads
~/Desktop
~/Documents
~/Library/Application Support
```

Artifacts:
- Downloaded malware  
- User‑launched scripts  
- Droppers and installers  

---

### Shell History

Files:
- `~/.zsh_history`  
- `~/.bash_history`  

Indicators:
- Manual execution  
- Command‑based persistence  
- Download commands  

---

## Authentication & Access Artifacts

### User Accounts

Data stored in:

```
/var/db/dslocal/
```

Artifacts:
- User creation  
- Group membership changes  

---

### Keychain

Stores:
- Passwords  
- Tokens  
- Certificates  

Forensics notes:
- Access requires user context  
- High‑value for credential theft cases  

---

### Permission Artifacts (TCC)

Database:

```
/Library/Application Support/com.apple.TCC/TCC.db
```

Artifacts:
- Granted permissions  
- App identifiers  
- Timestamps  

🚩 **Sudden permission grants are critical indicators.**

---

## Network‑Related Artifacts

Native logging is limited.

Sources include:
- Unified Logs  
- VPN client logs  
- Application‑specific logs  

**SOC Tip:**  
Correlate with firewall or proxy logs.

---

## Backup & Snapshot Artifacts

### Time Machine

Contains:
- Historical file states  
- Deleted artifacts  
- Timeline reconstruction  

### APFS Snapshots

Benefits:
- Point‑in‑time filesystem views  
- Recovery of removed persistence  

---

## Volatile Artifacts

- Running processes  
- Open network connections  
- Memory‑resident malware  

**SOC Reality:**  
Memory acquisition is difficult and limited.

---

## Incident Response Order (macOS)

1. Collect Unified Logs  
2. Enumerate persistence  
3. Capture running processes  
4. Review permissions (TCC)  
5. Identify user activity  
6. Correlate network indicators  

---

## Key Takeaways

- Logs are the most volatile evidence  
- Persistence artifacts are high value  
- User directories hold most malware  
- Permissions are forensic evidence  
- Speed matters on macOS investigations  

---
