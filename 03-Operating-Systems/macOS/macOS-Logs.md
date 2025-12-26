# macOS Logs — Sources, Locations & SOC Analysis (DFIR)



---

## Overview

Logging on macOS is **not file‑centric** like Linux and **not event‑centric** like Windows.

Instead, macOS uses a **hybrid model**:
- Unified Logging System (primary)  
- Limited traditional log files (secondary)  
- Application‑specific logs  
- Security & privacy‑driven filtering  

For SOC analysts, understanding **where logs exist and where they do not** is critical.

---

## macOS Logging Model (Big Picture)

macOS logging sources fall into four categories:

1. **Unified Logs** (primary, volatile)  
2. **Traditional log files** (limited)  
3. **Application‑specific logs**  
4. **Security & privacy databases**  

Most **high‑value events live only in Unified Logs**.

---

## 1. Unified Logging System (Primary)

Unified Logs capture:
- Process execution  
- Authentication  
- Permission usage  
- Security decisions  
- System events  

Accessed via:

```bash
log show
log stream
log collect
```

Characteristics:
- Binary format  
- Short retention  
- Privacy masking  
- Predicate‑based querying  

**SOC Reality:**  
If you miss Unified Logs, the evidence is gone.

---

## 2. Traditional Log Files (Secondary)

macOS still maintains some classic logs, but they are not comprehensive.

Common locations:

```
/var/log/system.log
/var/log/install.log
/var/log/appfirewall.log
```

### system.log  
Contains:
- General system messages  
- Limited security value  

### install.log  
Contains:
- Software installations  
- Package installs  
- Update activity  

🚩 **Useful for detecting malicious PKG installs.**

---

## 3. Authentication & Authorization Logs

Unlike Linux:

- No `/var/log/auth.log`

Authentication events appear in:
- Unified Logs  
- Security subsystems  

Relevant subsystems:
- `com.apple.authd`  
- `com.apple.sudo`  
- `com.apple.security`  

Example:

```bash
log show --predicate 'subsystem == "com.apple.authd"' --last 24h
```

---

## 4. Application‑Specific Logs

Many applications maintain their own logs.

Common locations:

```
~/Library/Logs
/Library/Logs
```

Examples:
- Browser logs  
- VPN client logs  
- EDR agent logs  
- Developer tools  

**SOC Tip:**  
These logs often survive longer than Unified Logs.

---

## 5. Security & Privacy Databases (Log‑Like Artifacts)

Some security events are recorded in databases, not logs.

### TCC Database

```
/Library/Application Support/com.apple.TCC/TCC.db
```

Tracks:
- Permission grants  
- User approvals  
- App identifiers  

### Configuration Profiles

```
/var/db/ConfigurationProfiles
```

Tracks:
- MDM actions  
- Policy enforcement  
- Profile installs  

🚩 **Changes here explain many “silent” behaviors.**

---

## 6. Firewall & Network Logs

### Application Firewall

Log file:

```
/var/log/appfirewall.log
```

Contains:
- Blocked/allowed app connections  
- Limited network context  

Limitations:
- No packet data  
- Minimal metadata  

---

## 7. SSH & Remote Access Logs

SSH events appear in:
- Unified Logs (primary)

There is **no dedicated SSH log file**.

Example:

```bash
log show --predicate 'process == "sshd"' --last 24h
```

---

## Log Retention Reality

Retention depends on:
- Disk space  
- System uptime  
- Log volume  
- macOS version  

Typical retention:
- **Hours to a few days**  
- Sometimes **minutes** under heavy load  

**SOC Rule:**  
Collect first, analyze later.

---

## Common SOC Use Cases

High‑value detections:
- GUI app spawning shell  
- Permission grants (TCC)  
- launchd persistence creation  
- SSH enablement  
- Software installs  
- Admin privilege usage  

All rely heavily on logs.

---

## Common Mistakes

- Searching for Linux‑style logs  
- Assuming logs persist  
- Ignoring application logs  
- Forgetting privacy masking  
- Delaying collection  

---

## Best Practices for SOC & DFIR

- Always collect Unified Logs early  
- Scope queries by time  
- Filter by subsystem  
- Correlate logs with filesystem artifacts  
- Use external telemetry (EDR, proxy, firewall)  

---

## Key Takeaways

- Unified Logs are the primary source of truth  
- Traditional logs are limited but useful  
- Many security events live in databases  
- Log retention is short and unforgiving  
- Speed and context matter most  

---
