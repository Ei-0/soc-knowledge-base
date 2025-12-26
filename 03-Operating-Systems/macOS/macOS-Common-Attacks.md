# macOS Common Attacks — Techniques, Vectors & SOC Detection

---

## Overview

macOS attacks focus on **user interaction, trust abuse, and stealth**, rather than kernel exploitation.

Attackers understand that:
- macOS users trust prompts  
- Signed apps appear safe  
- User permissions are powerful  
- EDR visibility is limited  

Most successful attacks require **no exploits**.

---

## Attack Surface Summary

Primary macOS attack surfaces:
- User trust & social engineering  
- Signed application abuse  
- GUI-based execution  
- Privacy permission prompts  
- Living-off-the-Land binaries (LOLBins)  

---

## 1. Malicious DMG & PKG Installers

### Description
Attackers distribute malware as:
- Fake applications  
- Cracked software  
- Trojanized installers  

Common delivery methods:
- Phishing emails  
- SEO poisoning  
- Fake download sites  

### Execution Flow
```
User opens DMG
→ User drags app to /Applications
→ User launches app
→ Malware executes under user context
```

🚩 **SOC Indicators:**
- Recently installed apps  
- Generic app names  
- Apps requesting excessive permissions  

---

## 2. Fake Software Updates

### Description
Fake prompts impersonate:
- macOS updates  
- Browser updates  
- Flash / Zoom / VPN updates  

Often delivered via:
- Malicious websites  
- Browser pop-ups  

### Why It Works
- Familiar Apple UI  
- Users conditioned to approve updates  

🚩 **Detection Clues:**
- Update prompts outside System Settings  
- Installers not signed by Apple  
- Sudden permission requests  

---

## 3. InfoStealers (High-Impact)

### Description
InfoStealers target:
- Browser credentials  
- Cookies  
- Keychain data  
- Crypto wallets  

Common goals:
- Account takeover  
- Session hijacking  
- Lateral movement  

### Execution Traits
- Runs silently  
- Exfiltrates via HTTPS  
- Often uses curl or custom clients  

🚩 **SOC Focus:**
- Browser process spawning network tools  
- Suspicious outbound connections  
- Access to Keychain APIs  

---

## 4. Signed Malware Abuse

### Description
Attackers abuse:
- Stolen developer certificates  
- Legitimate notarization  

Signed malware:
- Bypasses Gatekeeper  
- Appears legitimate to users  

🚩 **Red Flags:**
- Signed apps with abnormal behavior  
- Trusted apps spawning shells  
- Network activity from GUI apps  

---

## 5. Living-off-the-Land (LOLBins)

### Common macOS LOLBins
- osascript  
- launchctl  
- curl  
- bash / zsh  
- python  
- plutil  
- defaults  

### Abuse Example
```
osascript → download payload → execute
```

🚩 **Detection Strategy:**
- Parent-child anomalies  
- LOLBins launched by GUI apps  
- Execution from user directories  

---

## 6. Browser-Based Attacks

### Techniques
- Malicious extensions  
- Profile abuse  
- JavaScript-based droppers  

Targets:
- Safari  
- Chrome  
- Firefox  

🚩 **SOC Indicators:**
- New extensions  
- Modified browser preferences  
- Persistence without binaries  

---

## 7. Credential Access & Lateral Movement

### Methods
- Keychain access  
- Browser token theft  
- SSH key harvesting  

macOS often acts as:
- Initial access  
- Credential harvesting point  

---

## 8. Persistence-First Attacks

Attackers often:
1. Gain execution  
2. Establish persistence  
3. Steal data later  

Persistence gives:
- Time  
- Reliability  
- Reduced noise  

---

## Detection Priorities for SOC

High-signal behaviors:
- GUI apps spawning interpreters  
- Signed apps with malicious behavior  
- launchd persistence creation  
- Unexpected permission grants  
- Network tools executed by non-network apps  

---

## Incident Response Notes

- Focus on user context first  
- Identify persistence before containment  
- Collect Unified Logs early  
- Assume partial visibility  
- Remove persistence before killing processes  

---

## Key Takeaways

- macOS attacks are trust-based, not exploit-based  
- Signed does not mean safe  
- User permissions are powerful  
- Persistence is often subtle  
- Context beats signatures  

---
