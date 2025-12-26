# macOS Persistence Mechanisms — Techniques, Abuse & Detection (SOC / DFIR)



---

## Overview

Persistence on macOS is **primarily user‑space focused**.

Due to protections like:
- System Integrity Protection (SIP)
- Sealed System Volume (SSV)

Attackers rarely persist at the kernel or system binary level.  
Instead, they rely on **trusted macOS mechanisms** designed for legitimate automation.

---

## Core Persistence Principles on macOS

- Prefer user‑level persistence  
- Abuse trusted system frameworks  
- Blend into legitimate configuration  
- Avoid modifying protected system areas  

**SOC Reality:**  
User persistence is often enough for long‑term access.

---

## launchd — Primary Persistence Engine

`launchd` is the most common persistence mechanism on macOS.

It loads configuration files called **property lists (plists)**.

### LaunchAgents (User Context)

Paths:
```
~/Library/LaunchAgents
/Library/LaunchAgents
```

Characteristics:
- Runs as the user  
- Executes on login  
- Does not require root (user path)  

Common abuse:
- Background backdoors  
- InfoStealers  
- Periodic beaconing  

---

### LaunchDaemons (System Context)

Path:
```
/Library/LaunchDaemons
```

Characteristics:
- Runs as root  
- Executes at boot  
- Requires admin privileges  

🚩 Higher risk and higher visibility than LaunchAgents.

---

## plist Abuse Indicators

Red Flags:
- Plists referencing scripts in user‑writable paths  
- Suspicious `ProgramArguments`  
- `RunAtLoad` and `KeepAlive` set to true  
- Obfuscated command strings  

---

## Login Items

Login Items allow apps to start automatically when a user logs in.

Types:
- User‑added login items  
- Background items (newer macOS versions)  

Storage locations:
```
~/Library/Application Support/com.apple.backgroundtaskmanagementagent
```

**SOC Note:**  
Login Items are stealthy and user‑approved.

---

## Configuration Profiles

Profiles are powerful and dangerous.

Capabilities:
- Enforce system settings  
- Grant permissions  
- Install certificates  
- Enable VPNs  
- Control privacy settings  

Used by:
- MDM solutions  
- Enterprise management  

Attacker abuse:
- Install malicious profiles  
- Persist stealthily  
- Override security controls  

🚩 Profiles bypass many traditional detections.

---

## Cron & Legacy Mechanisms

Cron still exists but is deprecated.

Locations:
- User crontab  
- `/etc/crontab`  

**SOC Insight:**  
Cron persistence on macOS is uncommon and suspicious.

---

## rc Files & Shell Profiles

Persistence via shell initialization files:
- `~/.zshrc`  
- `~/.bash_profile`  
- `~/.bashrc`  

Common abuse:
- Command injection  
- Environment hijacking  

---

## Browser‑Based Persistence

Attackers may persist via:
- Browser extensions  
- Malicious profiles  
- Modified preferences  

Targets:
- Safari  
- Chrome  
- Firefox  

---

## TCC Persistence Abuse

Attackers aim to:
- Maintain granted permissions  
- Abuse Accessibility  
- Retain Full Disk Access  

Persistence **without binaries** is possible via permissions alone.

---

## Detection Strategies

Focus on:
- New or modified LaunchAgents/Daemons  
- Suspicious plists  
- Unexpected Login Items  
- Unauthorized configuration profiles  
- Modified shell init files  
- Persistence without binaries  

---

## Incident Response Tips

- Enumerate all launchd jobs  
- Review profile installations  
- Check Login Items per user  
- Correlate persistence with logs  
- Remove persistence before killing processes  

---

## Key Takeaways

- **launchd is the king of persistence**  
- User‑level persistence is the norm  
- Profiles are extremely powerful  
- Kernel persistence is rare  
- Context matters more than location  

---
