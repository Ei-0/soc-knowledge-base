# OSI Model (Open Systems Interconnection)

The OSI Model is a conceptual framework that explains how data moves across a network
in seven distinct layers. For SOC Analysts, the OSI model is critical for:
- Understanding where attacks occur
- Mapping alerts to the correct layer
- Identifying which logs to analyze during investigations

---

## 1. Why the OSI Model Matters in SOC
Most security alerts can be mapped to a specific OSI layer.
If you know **which layer is affected**, you immediately know:
- What type of attack is happening
- Which tools/logs to check
- How deep the investigation should go

> **SOC Rule:**  
> Identify the OSI layer → Identify the attack → Identify the evidence.

---
<img width="560" height="516" alt="image" src="https://github.com/user-attachments/assets/e154f274-e215-4031-9e85-a81633ea26b8" />

## 2. OSI Model Overview

Layer | Name | Key Focus
----- | ---- | ---------
7 | Application | User-facing services
6 | Presentation | Data formatting & encryption
5 | Session | Session management
4 | Transport | End-to-end communication
3 | Network | Routing & IP addressing
2 | Data Link | MAC addressing & switching
1 | Physical | Physical transmission

---
<img width="800" height="1040" alt="image" src="https://github.com/user-attachments/assets/4675053d-9623-485c-8325-1e007ad65195" />

## 3. Layer 7 – Application Layer

### Description
The Application layer is where users interact with network services.

### Common Protocols
- HTTP / HTTPS
- DNS
- FTP
- SMTP / IMAP / POP3
- SMB

### Common Attacks
- SQL Injection
- Cross-Site Scripting (XSS)
- Command Injection
- Phishing
- Malware downloads

### SOC Logs to Analyze
- Web server logs
- Proxy logs
- DNS logs
- Email security logs

### SOC Example
A user downloads a malicious file from a suspicious website → **Layer 7 alert**.

---

## 4. Layer 6 – Presentation Layer

### Description
Handles data formatting, compression, and encryption.

### Common Technologies
- SSL / TLS
- Encoding formats (ASCII, Unicode)

### Common Attacks
- SSL stripping
- Weak encryption exploitation
- Certificate abuse

### SOC Logs to Analyze
- TLS inspection logs
- Firewall SSL logs
- Proxy inspection logs

### SOC Insight
Encrypted traffic does NOT mean safe traffic.

---

## 5. Layer 5 – Session Layer

### Description
Manages sessions between applications.

### Common Functions
- Session establishment
- Session maintenance
- Session termination

### Common Attacks
- Session hijacking
- Session fixation
- Token reuse

### SOC Logs to Analyze
- Authentication logs
- VPN logs
- Application session logs

---

## 6. Layer 4 – Transport Layer

### Description
Ensures reliable or fast data delivery between hosts.

### Common Protocols
- TCP
- UDP

### Common Attacks
- SYN Flood
- UDP Flood
- Port exhaustion
- Connection abuse

### SOC Logs to Analyze
- Firewall connection logs
- IDS/IPS alerts
- NetFlow data

### SOC Insight
Abnormal connection behavior often signals DoS or malware activity.

---

## 7. Layer 3 – Network Layer

### Description
Responsible for routing packets between networks.

### Common Protocols
- IP
- ICMP
- IPSec

### Common Attacks
- ICMP tunneling
- IP spoofing
- Route manipulation

### SOC Logs to Analyze
- Router logs
- Firewall traffic logs
- NetFlow / sFlow

---

## 8. Layer 2 – Data Link Layer

### Description
Handles communication within the same network segment.

### Common Technologies
- Ethernet
- ARP
- MAC addressing

### Common Attacks
- ARP Spoofing
- MAC flooding
- VLAN hopping

### SOC Logs to Analyze
- Switch logs
- NAC logs
- ARP tables

---

## 9. Layer 1 – Physical Layer

### Description
Transmits raw bits over physical media.

### Examples
- Network cables
- Fiber optics
- Wireless signals

### Common Attacks
- Cable tapping
- Hardware tampering
- Signal jamming

### SOC Logs to Analyze
- Physical access logs
- Device status alerts

---

## 10. OSI Model from a SOC Investigation Perspective
<img width="2391" height="2435" alt="image" src="https://github.com/user-attachments/assets/23888e2e-30bc-4d0f-bd79-7e679e58f9a1" />

Incident Type | Likely OSI Layer
------------- | ----------------
Phishing Email | Layer 7
DDoS Attack | Layer 4
Lateral Movement | Layer 2 / 3
C2 Communication | Layer 7
Data Exfiltration | Layer 7 / 4

---

## 11. Common SOC Mistake
❌ Investigating alerts without identifying the OSI layer  
✅ Always start by mapping the alert to the OSI layer

---

## 12. Summary
The OSI Model provides a structured way to:
- Understand network communication
- Analyze attacks efficiently
- Choose the right logs and tools

> **Master the OSI Model, and you master SOC investigations.**
