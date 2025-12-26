# macOS Architecture — Security Internals for SOC & DFIR



---

## Overview

Understanding macOS architecture is critical for SOC analysts because Apple’s design choices directly affect:
- Visibility
- Detection
- Forensic acquisition
- EDR capabilities

macOS is built to **protect the user first**, not the enterprise defender.

---

## High-Level Architecture

macOS consists of multiple tightly integrated layers:

```
User Applications
│
├── Cocoa / Carbon / SwiftUI
│
├── User Space Services
│   ├── launchd
│   ├── WindowServer
│   ├── SystemUIServer
│
├── BSD Layer
│   ├── Filesystem
│   ├── Networking
│   ├── Permissions
│
├── Mach Kernel
│   ├── IPC
│   ├── Scheduling
│   ├── Memory Management
│
└── Hardware
```

At the core is the **XNU Kernel**.

---

## XNU Kernel (Hybrid Model)

XNU = **X is Not Unix**

### Components:

- **Mach**
  - Process scheduling  
  - Memory management  
  - Inter-process communication (IPC)

- **BSD**
  - POSIX compliance  
  - Filesystem  
  - Networking  
  - Users & permissions  

- **IOKit**
  - Device drivers  
  - Hardware abstraction  

### SOC Impact
- Kernel hooks are restricted  
- Traditional rootkits are harder to deploy  
- Memory visibility is limited  

---

## System Integrity Protection (SIP)

SIP prevents even root from modifying critical areas.

### Protected locations include:
- /System  
- /usr (except /usr/local)  
- /bin  
- /sbin  
- Kernel extensions  

### SIP also restricts:
- Debugging system processes  
- Runtime code injection  
- Kernel modification  

### Detection Insight
If malware bypasses SIP, it indicates:
- Advanced exploitation  
- Kernel-level vulnerability  
- Signed malicious components  

---

## Gatekeeper & Notarization

### Gatekeeper
- Enforces execution policy  
- Blocks unsigned or untrusted binaries  
- Applies to:
  - DMG  
  - PKG  
  - App bundles  

### Notarization
- Apple scans software for malware  
- Signed binaries gain higher trust  
- Attackers abuse stolen certificates  

### SOC Red Flags
- Signed malware behaving abnormally  
- Notarized apps spawning shells or network tools  

---

## TCC (Transparency, Consent, and Control)

TCC controls access to sensitive resources:
- Full Disk Access  
- Camera  
- Microphone  
- Screen Recording  
- Accessibility  
- Files & folders  

Stored in:

```
/Library/Application Support/com.apple.TCC/TCC.db
```

### Attacker Abuse
- Modifying TCC.db (if permissions allow)  
- Social engineering user approvals  
- Living-off-the-land via trusted apps  

---

## Endpoint Security Framework (ESF)

Apple-approved interface for security tools.

### Capabilities:
- Process execution events  
- File operations  
- Network activity (limited)  
- Code signing metadata  

### Limitations:
- No kernel hooking  
- User approval required  
- Less telemetry than Windows  

### SOC Reality
macOS EDR:
- Sees less  
- Detects later  
- Relies heavily on behavior  

---

## launchd — The Root of Execution

`launchd` is PID 1 on macOS.

### Responsibilities:
- Process spawning  
- Service management  
- Persistence loading  

Every process traces back to:

```
launchd (PID 1)
```

Abuse of launchd = high-confidence persistence.

---

## Security Design Philosophy (Important)

Apple prioritizes:
1. User privacy  
2. System integrity  
3. Developer trust  

SOC visibility is **not** a priority.

This explains:
- Limited logging retention  
- User-consent-driven access  
- Restricted kernel visibility  

---

## Key Takeaways for SOC Analysts

- macOS is **not Linux with a GUI**  
- Root access does not equal full control  
- Persistence is subtle and user-space focused  
- Signed malware is more dangerous than unsigned  
- Detection requires deep platform knowledge  
