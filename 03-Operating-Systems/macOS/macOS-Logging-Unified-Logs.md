# macOS Unified Logging — Collection, Analysis & Detection (SOC / DFIR)



---

## Overview

macOS uses the **Unified Logging System**, which is fundamentally different from:
- Windows Event Logs  
- Linux text-based logs  

For SOC and DFIR teams, this is one of the **most challenging aspects** of macOS investigations.

Logs are:
- Binary  
- Ephemeral  
- Privacy-aware  
- Strongly filtered by default  

Missed logs are often **lost forever**.

---

## What Is Unified Logging?

Unified Logging is a centralized logging pipeline introduced by Apple to:
- Improve performance  
- Protect user privacy  
- Reduce disk usage  

### Characteristics:
- Logs stored in binary format  
- Centralized log store  
- Heavy use of metadata  
- Access-controlled output  

---

## Log Storage

Logs are stored in:

```
/private/var/db/diagnostics
/private/var/db/uuidtext
/private/var/log
```

However:
- Files are **not human-readable**  
- Direct access is rarely useful  
- Analysis is performed via the `log` utility  

---

## Primary Log Access Tool

The main interface is the `log` command.

### Core Commands

```bash
log show
log stream
log collect
```

- `log show` → historical logs  
- `log stream` → real-time logs  
- `log collect` → diagnostic bundle  

---

## log show — Historical Analysis

Basic example:

```bash
log show --last 1h
```

Filtered example:

```bash
log show --predicate 'process == "ssh"' --last 24h
```

### Common filters:
- process  
- subsystem  
- category  
- eventMessage  

**SOC Tip:**  
Always scope by time to avoid massive output.

---

## log stream — Real-Time Monitoring

Example:

```bash
log stream --predicate 'process == "sudo"'
```

### Use cases:
- Incident response  
- Live attack monitoring  
- Permission abuse detection  

### Limitations:
- No historical data  
- Requires active session  

---

## Privacy Levels

Logs are tagged with privacy levels:
- public  
- private  
- sensitive  

By default:
- Private fields are masked  
- Full visibility requires elevated privileges  

🚩 Some attacker actions may be intentionally obscured.

---

## Log Retention (Critical)

macOS log retention is **short and variable**.

Factors affecting retention:
- Disk space  
- System uptime  
- Log volume  
- Privacy settings  

**SOC Reality:**  
Retention may be **hours, not days**.  
Rapid response is essential.

---

## Important Log Sources for SOC

### Authentication & Authorization
- sudo usage  
- privilege escalation  
- Touch ID events  
- Login attempts  

### Process Execution
- exec events  
- Code signing failures  
- Quarantine events  

### Persistence & Configuration
- launchd activity  
- Profile installation  
- System settings changes  

### Network Indicators
- Limited visibility  
- Some VPN and network events  

---

## Subsystems (Key Concept)

Subsystems group related logs.

Examples:
- `com.apple.security`  
- `com.apple.sudo`  
- `com.apple.launchd`  
- `com.apple.TCC`  
- `com.apple.authd`  

Filtering by subsystem is often more effective than filtering by process name.

---

## TCC & Privacy Logging

TCC-related events include:
- Permission prompts  
- User approvals  
- Access denials  

Example filter:

```bash
log show --predicate 'subsystem == "com.apple.TCC"' --last 24h
```

🚩 Sudden permission grants are **high-signal events**.

---

## Common Detection Use Cases

- GUI apps triggering sudo  
- launchd spawning unsigned binaries  
- Accessibility permission abuse  
- Full Disk Access grants  
- Repeated authentication failures  
- Execution from user-writable paths  

---

## Forensics Challenges

- Logs rotate quickly  
- Binary format  
- Privacy masking  
- User consent affects visibility  
- No central event viewer  

**Best practice:**
- Collect logs early  
- Export during live response  
- Correlate with filesystem artifacts  

---

## SOC Best Practices

- Learn predicate-based filtering  
- Focus on high-signal subsystems  
- Combine logs with process trees  
- Treat logs as volatile evidence  
- Assume partial visibility  

---

## Key Takeaways

- Unified Logs are powerful but unforgiving  
- Retention is short  
- Context and timing are everything  
- Subsystems matter more than files  
- macOS logging favors privacy over detection  
