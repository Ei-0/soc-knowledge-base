# macOS Networking — Stack, Visibility & SOC Detection (DFIR)



---

## Overview

Networking on macOS is **BSD-based** but heavily abstracted and privacy‑aware.

From a SOC perspective:
- Native network logging is limited  
- Visibility depends on user‑space events  
- Many network actions occur inside GUI apps  

macOS networking investigations require **correlation**, not single data sources.

---

## macOS Networking Stack

macOS networking is built on:
- BSD networking stack  
- XNU kernel networking components  
- User‑space frameworks  

High‑level flow:

```
Application
→ Network Frameworks
→ BSD Socket Layer
→ Kernel Networking
→ Network Interface
```

**SOC Impact:**
- Kernel‑level visibility is restricted  
- User‑space context is critical  

---

## Network Interfaces

Common interfaces:
- **en0** (Wi‑Fi)  
- **en1** (Ethernet)  
- **lo0** (Loopback)  
- **utun\*** (VPN tunnels)  

**SOC Tip:**  
`utun` interfaces often indicate VPN or tunneling activity.

---

## Network Configuration Artifacts

Stored in:

```
/Library/Preferences/SystemConfiguration/
```

Key files:
- `preferences.plist`  
- `NetworkInterfaces.plist`  

Artifacts include:
- Interface changes  
- DNS configuration  
- Proxy settings  

🚩 **Unexpected proxy settings are high‑signal.**

---

## Packet Filtering (pf)

macOS uses **pf (Packet Filter)** for firewalling.

Configuration:

```
/etc/pf.conf
```

Characteristics:
- Disabled by default for monitoring  
- Limited logging  
- Not commonly used by attackers  

**SOC Note:**  
pf is rarely abused for persistence.

---

## Application‑Level Networking

Most network activity occurs inside:
- Browsers  
- GUI applications  
- Background agents  

Examples:
- Safari  
- Chrome  
- Mail  
- Electron apps  

🚩 **GUI apps initiating unusual outbound connections are high risk.**

---

## Network Tools & LOLBins

Built‑in tools abused by malware:
- curl  
- nc  
- ping  
- scp  
- ssh  

**SOC Detection:**
- These tools executed by non‑terminal parents  
- Network utilities spawned by GUI apps  

---

## Unified Logs & Networking

Network‑related events may appear in:
- `com.apple.network`  
- `com.apple.networking`  
- Application‑specific subsystems  

Example filter:

```bash
log show --predicate 'subsystem CONTAINS "network"' --last 1h
```

Limitations:
- No full packet visibility  
- Metadata only  

---

## VPN & Tunneling

VPN clients create:
- `utun` interfaces  
- Encrypted tunnels  

Artifacts:
- VPN logs  
- Unified Logs  
- Configuration profiles  

🚩 **Unauthorized VPN usage can indicate data exfiltration.**

---

## DNS & Proxy Abuse

Attackers may:
- Modify DNS settings  
- Install malicious proxies  
- Redirect traffic  

Artifacts:
- SystemConfiguration plists  
- Browser proxy settings  

---

## Command‑and‑Control Patterns

Common C2 traits on macOS:
- HTTPS over port 443  
- Cloud service abuse  
- Low‑and‑slow beaconing  

**SOC Strategy:**  
Detect **behavior**, not destination alone.

---

## Detection Strategies

Focus on:
- GUI apps with outbound connections  
- Network tools spawned unexpectedly  
- DNS or proxy changes  
- VPN interfaces appearing unexpectedly  
- Network activity shortly after login  

---

## Forensics & IR Considerations

- Network evidence is limited locally  
- Correlate with firewall, proxy, and EDR logs  
- Capture live connections early  
- Assume incomplete visibility  

---

## Key Takeaways

- macOS networking visibility is limited  
- User‑space context is critical  
- GUI‑based networking is attacker‑friendly  
- Correlation is mandatory  
- Behavior beats packet inspection  

---
