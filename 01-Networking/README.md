# 01 - Networking

This section covers the core networking knowledge required for a Security
Operations Center (SOC) Analyst. Networking is the foundation of detection,
investigation, and incident response.

Almost every cyber attack leaves a network footprint.
Understanding how networks operate allows SOC Analysts to identify abnormal
behavior, trace attacker movement, and reconstruct attack timelines.

---

## 🎯 Objectives of This Section
By completing this section, you will be able to:
- Understand how network communication works
- Identify normal vs abnormal network traffic
- Analyze network logs effectively
- Detect network-based attacks
- Correlate alerts using OSI and TCP/IP models

---
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/d6094f9c-acb9-4119-a887-c240e18ab57c" />

## 📚 Contents

- Networking Basics
- OSI Model (Security Mapping)
- TCP/IP Model
- Traffic Flow Analysis (North–South / East–West)
- Common Network Ports
- Network Logs
- Network-Based Attacks
- Defensive Network Controls
- Network Devices
- Network Protocols Overview
- Subnetting & Segmentation

Each topic is written from a **SOC Analyst perspective**, focusing on detection,
logs, and investigation rather than pure theory.

---

## 🧭 Quick Reference — OSI + TCP/IP + Traffic Flow




### How SOC Analysts Use This Mapping
| Alert Type | OSI Layer | TCP/IP Layer | Traffic Direction |
|----------|-----------|--------------|-------------------|
| DNS Anomaly | Layer 7 | Application | Outbound |
| SYN Flood | Layer 4 | Transport | Inbound |
| SMB Lateral Movement | Layer 2/3 | Network Access | East–West |
| HTTPS C2 | Layer 7 | Application | Outbound |

> **SOC Mental Model:**  
> Layer + Direction + Protocol = Faster Investigation
<img width="1200" height="1384" alt="image" src="https://github.com/user-attachments/assets/941f0503-0396-4210-8b8a-04352050403f" />

---

## 🧪 Mini SOC Scenarios (Networking)

### Scenario 01 — Suspicious DNS Beaconing
**Alert:** High-frequency DNS queries to random domains  
**Analysis:**  
- OSI Layer: 7  
- TCP/IP Layer: Application  
- Traffic: Outbound (North–South)  
**Suspicion:** DNS Tunneling / C2  
**Action:** Block domain, isolate host, start IR

---

### Scenario 02 — Internal RDP Connection
**Alert:** RDP traffic between user and server subnet  
**Analysis:**  
- OSI Layer: 4  
- TCP/IP Layer: Transport  
- Traffic: East–West  
**Suspicion:** Lateral Movement  
**Action:** Validate access, check credentials, monitor spread

---

### Scenario 03 — Large Outbound HTTPS Transfer
**Alert:** 8GB HTTPS upload at unusual hours  
**Analysis:**  
- OSI Layer: 7  
- TCP/IP Layer: Application  
- Traffic: Outbound  
**Suspicion:** Data Exfiltration  
**Action:** Block destination, preserve logs, escalate severity

---

### Scenario 04 — External Port Scan
**Alert:** Multiple ports scanned in short time  
**Analysis:**  
- OSI Layer: 4  
- TCP/IP Layer: Transport  
- Traffic: Inbound  
**Suspicion:** Reconnaissance  
**Action:** Block source IP, monitor targets

---

## 🧠 SOC Analyst Takeaway
- Network alerts are meaningless without context
- Traffic flow reveals attacker behavior
- Internal traffic is just as dangerous as external
- Segmentation and subnet awareness are critical

> **If you understand the network, you can understand the attack.**

---

## 🚀 What’s Next?
After completing this section, the next logical step is:
**02 - Protocols**, where each protocol (DNS, HTTP/S, SMB, RDP) is analyzed
deeply from an attack and detection perspective.

---
