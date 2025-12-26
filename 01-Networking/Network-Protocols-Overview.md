# Network Protocols Overview

Network protocols define how data is formatted, transmitted, and received
across networks. SOC Analysts must understand protocol behavior to identify
abuse, misconfigurations, and malicious activity.

This document provides a high-level overview before diving into protocol-specific
analysis in later sections.

---

## 1. Why Protocol Knowledge Matters in SOC
Every network alert references a protocol.
If you understand the protocol, you can answer:
- Is this behavior normal?
- Is this protocol being abused?
- What attack stage does this indicate?

> **SOC Rule:**  
> Abnormal protocol behavior is often more important than the alert itself.

---

## 2. TCP vs UDP
<img width="2048" height="1104" alt="image" src="https://github.com/user-attachments/assets/4039da92-322e-4516-a02a-a126480222b9" />

### TCP (Transmission Control Protocol)
- Connection-oriented
- Reliable delivery
- Error checking and retransmission

Common Uses:
- HTTP / HTTPS
- SMTP
- FTP
- SMB

SOC Relevance:
- SYN floods
- Session abuse
- Connection exhaustion

---

### UDP (User Datagram Protocol)
- Connectionless
- Faster, no delivery guarantee

Common Uses:
- DNS
- NTP
- VoIP
- Streaming

SOC Relevance:
- DDoS amplification
- DNS tunneling
- Lack of session tracking

---

## 3. HTTP / HTTPS

### Description
Protocols used for web communication.

Common Uses:
- Web browsing
- API communication
- Cloud services

SOC Abuse Cases:
- Malware delivery
- C2 communication
- Data exfiltration

Logs to Monitor:
- Proxy logs
- Web server logs
- Firewall logs

SOC Indicator:
- Rare domains
- Abnormal HTTP methods
- Large POST requests

---

## 4. DNS (Domain Name System)

### Description
Resolves domain names to IP addresses.

SOC Abuse Cases:
- DNS tunneling
- Malware beaconing
- Domain generation algorithms (DGA)

Logs to Monitor:
- DNS query logs
- Response logs

SOC Indicator:
- Long or random domains
- High query frequency
- NXDOMAIN spikes

---

## 5. SMB (Server Message Block)

### Description
File sharing and internal communication protocol.

SOC Abuse Cases:
- Lateral movement
- Ransomware propagation
- Credential harvesting

Logs to Monitor:
- Firewall logs
- Authentication logs
- File access logs

SOC Indicator:
- Unexpected SMB traffic
- One host accessing many systems

---

## 6. RDP (Remote Desktop Protocol)

### Description
Provides remote graphical access to systems.

SOC Abuse Cases:
- Brute-force attacks
- Credential abuse
- Hands-on-keyboard attacks

Logs to Monitor:
- Authentication logs
- Firewall logs
- VPN logs

SOC Indicator:
- Login attempts outside business hours
- RDP from non-admin users

---

## 7. Email Protocols (SMTP, POP3, IMAP)
<img width="2400" height="1884" alt="image" src="https://github.com/user-attachments/assets/9342b1b4-b6ca-4201-becb-b75983a27640" />

### Description
Protocols used to send and receive email.

SOC Abuse Cases:
- Phishing
- Malware attachments
- Account compromise

Logs to Monitor:
- Email gateway logs
- Authentication logs

SOC Indicator:
- Suspicious attachments
- Unusual login locations

---

## 8. ICMP

### Description
Used for network diagnostics.

SOC Abuse Cases:
- Network scanning
- ICMP tunneling

Logs to Monitor:
- Firewall logs
- IDS alerts

SOC Indicator:
- Excessive ICMP requests
- ICMP payloads with data

---

## 9. Protocol Abuse Summary

Protocol | Legitimate Use | Common Abuse
-------- | -------------- | ------------
HTTP/S | Web traffic | C2, exfiltration
DNS | Name resolution | Tunneling, beaconing
SMB | File sharing | Lateral movement
RDP | Remote admin | Unauthorized access
SMTP | Email delivery | Phishing
ICMP | Diagnostics | Scanning, tunneling

---

## 10. SOC Analyst Mindset
❌ Focus only on IP addresses  
✅ Understand protocol behavior  

> **When attackers hide, they hide inside legitimate protocols.**

---

## 11. Summary
Network protocols are the language of the network.
SOC Analysts who understand protocol behavior can:
- Detect stealthy attacks
- Identify misuse of legitimate services
- Respond faster and more accurately

> **Learn the protocol, uncover the threat.**
