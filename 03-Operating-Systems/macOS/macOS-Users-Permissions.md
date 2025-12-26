# macOS Users & Permissions — Identity, Access & Abuse (SOC / DFIR)



---

## Overview

User accounts and permission controls on macOS are **central to both security and attacker success**.

Unlike Linux, macOS tightly integrates:
- User identity  
- GUI permissions  
- Privacy controls  
- System protections  

Attackers rarely need root if they can **abuse user permissions effectively**.

---

## macOS User Account Types

macOS supports several account types:

### Standard User
- Default account type  
- Limited system changes  
- Can install apps (with password)  

### Administrator
- Member of the `admin` group  
- Can install system software  
- Can grant permissions to apps  
- Does **NOT** bypass SIP  

### Root User
- Disabled by default  
- Rarely used interactively  
- Still restricted by SIP  

🚩 **Root access ≠ full control on macOS.**

---

## User & Group Model

macOS uses a BSD-style user model.

### Key groups:
- admin  
- staff  
- wheel  
- everyone  

Group membership impacts:
- sudo access  
- GUI prompts  
- App installation behavior  

**SOC Tip:**  
Unexpected admin membership is high risk.

---

## Authentication Mechanisms

Common authentication methods:
- Local password  
- FileVault unlock  
- Touch ID  
- Apple ID (iCloud integration)  

Artifacts:
- `/var/db/dslocal/`  
- Keychain  
- Authentication logs (Unified Logs)  

---

## Permissions Layers (Stacked Model)

macOS permissions operate in layers:

1. POSIX permissions  
2. Access Control Lists (ACLs)  
3. System Integrity Protection (SIP)  
4. TCC privacy permissions  
5. User consent dialogs  

Bypassing one layer does **not** bypass the others.

---

## Access Control Lists (ACLs)

ACLs provide fine‑grained permissions beyond POSIX.

Example:
```bash
ls -le
```

ACLs are common on:
- User home directories  
- Application folders  
- Shared resources  

🚩 **Malicious ACL changes can enable stealth access.**

---

## TCC — Privacy Permissions

TCC governs access to sensitive resources:
- Full Disk Access  
- Screen Recording  
- Accessibility  
- Camera and Microphone  
- Files and folders  

Stored in:

```
/Library/Application Support/com.apple.TCC/TCC.db
```

### Attackers abuse TCC by:
- Social engineering user approval  
- Abusing trusted applications  
- Modifying TCC database (if possible)  

---

## Sudo on macOS

- Admin users can use `sudo`  
- `sudo` still respects SIP  
- Sudo activity is logged via Unified Logs  

**SOC Insight:**  
Sudo usage on **non‑technical users** is suspicious.

---

## FileVault & Disk Encryption

**FileVault:**
- Encrypts the entire disk  
- Protects data at rest  
- Requires user credentials at boot  

### Forensics Impact:
- Live response preferred  
- Disk imaging requires credentials or recovery keys  

---

## Common Abuse Scenarios

Attackers may:
- Elevate a standard user to admin  
- Abuse Accessibility permissions  
- Grant Full Disk Access to malicious apps  
- Leverage user consent to bypass controls  

---

## Detection Strategies

Monitor for:
- Admin group membership changes  
- New Accessibility or FDA grants  
- TCC database modifications  
- Unexpected sudo usage  
- Suspicious login patterns  

---

## Key Takeaways

- User permissions are the primary attack surface  
- Root access is less valuable than on Linux  
- TCC is a major defender **and** attacker focus  
- User consent is a security boundary  
- Visibility depends on Unified Logs  
