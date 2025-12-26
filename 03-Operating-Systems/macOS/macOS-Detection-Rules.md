# macOS Detection Rules — Behavioral Signals & SOC Use Cases (DFIR)


---

## Overview

Detection on macOS is **behavior‑driven**, not signature‑driven.

Because of:
- Limited kernel telemetry  
- Short log retention  
- Strong privacy controls  

SOC teams must rely on **high‑signal behaviors, context, and correlations**.

---

## Detection Philosophy (macOS)

Effective macOS detection focuses on:
- Parent–child process anomalies  
- Abuse of trusted components  
- Permission changes  
- Persistence creation  
- Timing and user context  

Key mindset:
> Assume you never see everything.

---

## High-Signal Detection Categories

### 1. Process Anomalies

#### Suspicious Parent–Child Relationships

Examples:
```
Finder → bash
Safari → osascript
SystemUIServer → curl
```

Detection Logic:
- GUI app spawning shell or interpreter  
- GUI app spawning network utilities  

**Signal Level: HIGH**

---

### 2. launchd Abuse (Persistence)

Detect creation or modification of:
- LaunchAgents  
- LaunchDaemons  

Indicators:
- New plist files  
- RunAtLoad enabled  
- ProgramArguments pointing to user‑writable paths  

**Signal Level: VERY HIGH**

---

### 3. Execution from User-Writable Paths

Paths of interest:
- `~/Downloads`  
- `~/Desktop`  
- `~/Library/Application Support`  
- `/tmp`  
- `/private/tmp`  

Detection Logic:
- Executables launched from non‑standard locations  

**Signal Level: HIGH**

---

### 4. Living-off-the-Land (LOLBins) Abuse

Common binaries:
- osascript  
- curl  
- bash / zsh  
- python  
- plutil  
- defaults  

Detection Context:
- Executed by GUI apps  
- Executed shortly after login  
- Executed repeatedly in short intervals  

**Signal Level: MEDIUM → HIGH**

---

## Permission-Based Detections (TCC)

### Accessibility Abuse

Detect:
- New Accessibility grants  
- Accessibility granted to non‑assistive apps  

**Signal Level: VERY HIGH**

---

### Full Disk Access Grants

Detect:
- FDA granted outside MDM  
- FDA granted to user‑downloaded apps  

**Signal Level: VERY HIGH**

---

## Authentication & Privilege Abuse

Detect:
- Unexpected sudo usage  
- Admin group membership changes  
- Remote Login (SSH) enabled  

Indicators:
- Unified Logs  
- System configuration changes  

**Signal Level: HIGH**

---

## Network-Based Detections

### Suspicious Outbound Activity

Detect:
- GUI apps initiating outbound HTTPS  
- Network connections immediately after login  
- Rare domains contacted by non‑browser apps  

**Signal Level: MEDIUM**

---

## Timing-Based Detections

High‑risk timing:
- Immediately after user login  
- Shortly after permission grants  
- After reboot  
- Outside business hours  

**Context elevates weak signals.**

---

## Example Detection Logic (Pseudo)

```
IF
  ParentProcess IN (Finder, Safari, SystemUIServer)
AND
  ChildProcess IN (bash, zsh, osascript, curl, python)
THEN
  Alert: Suspicious GUI-to-CLI Execution
```

---

## Threat Hunting Hypotheses (macOS)

- Which GUI apps spawned shells this week?  
- Which users granted Accessibility recently?  
- Which LaunchAgents were added in the last 7 days?  
- Which signed apps show abnormal behavior?  
- Which endpoints enabled SSH unexpectedly?  

---

## False Positives Considerations

Common benign sources:
- Developers  
- IT admins  
- Automation tools  
- MDM activity  

Mitigation:
- User role awareness  
- Device role awareness  
- Time‑of‑day correlation  

---

## Detection Gaps (Reality Check)

macOS limitations:
- No full command‑line visibility  
- Limited network telemetry  
- Short log retention  
- User‑approved blind spots  

Design detections assuming:
> Partial data is normal.

---

## SOC Best Practices

- Prioritize high‑signal behaviors  
- Correlate process + persistence + permissions  
- Alert on changes, not static states  
- Tune per user role  
- Respond quickly to collect logs  

---

## Key Takeaways

- macOS detection is behavior‑first  
- Persistence and permissions are top signals  
- Context elevates weak indicators  
- Assume incomplete visibility  
- Speed matters more than depth  

---
