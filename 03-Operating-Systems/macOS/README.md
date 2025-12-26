# macOS Security — SOC & DFIR Guide



---

## Overview

macOS is increasingly common in enterprise environments, especially among:
- Executives (VIP targets)
- Developers
- Security & engineering teams

As adoption grows, attackers actively target macOS, making it critical for SOC analysts and DFIR teams to understand its unique architecture, logging model, and persistence mechanisms.

Unlike Windows and Linux, macOS introduces strong platform protections that significantly impact detection, visibility, and response.

---

## Why macOS Matters for SOC Analysts

- macOS endpoints often hold high-value credentials  
- Increasing number of macOS-specific malware families  
- Apple security controls restrict traditional EDR techniques  
- Logging and persistence differ radically from Linux and Windows  

---

## macOS Security Architecture (High-Level)

Key security components include:

- XNU Kernel (Hybrid: Mach + BSD)
- System Integrity Protection (SIP)
- Gatekeeper
- Notarization
- TCC (Transparency, Consent, and Control)
- Endpoint Security Framework (ESF)

These controls reduce attacker flexibility but also limit defender visibility.

---

## Logging Model (Unified Logging)

macOS does not rely on traditional text-based logs such as:
- /var/log/auth.log
- /var/log/syslog

Instead, it uses the Unified Logging System:
- Binary log storage  
- Accessed via:

```bash
log show
log stream
```

### SOC Impact
- Logs are ephemeral  
- Requires filtering by process, subsystem, or predicate  
- Missed logs are permanently lost  

---

## Process Model & Execution Flow

Parent-child relationships are critical.

Common trusted parents abused by attackers:
- launchd
- Finder
- SystemUIServer
- osascript

### Example:
```
launchd
 └── Finder
     └── bash
         └── curl
```

### Red Flag:
GUI applications spawning shells or network tools.

---

## Persistence Mechanisms (macOS-Specific)

Common persistence locations:

- ~/Library/LaunchAgents  
- /Library/LaunchDaemons  
- Login Items  
- Configuration Profiles  
- Cron (legacy, limited)  
- TCC database abuse  

Attackers prefer signed or user-space persistence to bypass SIP.

---

## Common macOS Attacks

- Malicious DMG and PKG installers  
- Fake software updates  
- InfoStealers targeting browsers and Keychain  
- Signed malware abusing Apple trust model  
- Living-off-the-Land techniques using:
  - osascript  
  - launchctl  
  - plutil  
  - defaults  

---

## Forensics Challenges on macOS

- SIP restricts disk and memory access  
- Full Disk Access is required for most tools  
- Unified logs are volatile  
- Memory acquisition is limited  
- User consent heavily impacts visibility  

---

## SOC Analyst Learning Path

Recommended order:

1. macOS Architecture  
2. Processes and Execution  
3. File System and Permissions  
4. Unified Logging  
5. Persistence Mechanisms  
6. Common Attacks  
7. Malware Techniques  
8. Forensics Artifacts  
9. Incident Response  
10. Detection Rules and EDR Reality  

---

## Comparison (SOC Perspective)

| Feature     | Windows     | Linux            | macOS          |
|-------------|-------------|------------------|----------------|
| Logging     | Event Logs  | Text Logs        | Unified Logs   |
| Persistence | Registry    | Cron / Services  | LaunchAgents   |
| Kernel      | NT          | Monolithic       | Hybrid (XNU)   |
| EDR Access  | Full        | Medium           | Restricted     |

---

## Key Takeaway

macOS prioritizes user privacy and system integrity.  
This reduces attacker capabilities while simultaneously limiting SOC visibility.

Effective defense on macOS requires platform-specific knowledge, not Windows-based assumptions.
