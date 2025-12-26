# 02 - Network Protocols (SOC Knowledge Base)

This section focuses on **network and security protocols** from a **SOC analyst perspective**.  
Understanding protocol behavior is essential for detecting attacks, investigating alerts, and performing threat hunting.

Almost every security alert is tied to **protocol usage and behavior**.

---

## Section Objectives
By the end of this section, you should be able to:
- Understand how common protocols operate
- Identify normal vs abnormal protocol behavior
- Analyze protocol-related logs and alerts
- Detect protocol abuse used in real-world attacks
- Apply protocol knowledge during SOC investigations

---
<img width="1444" height="1882" alt="image" src="https://github.com/user-attachments/assets/0ad6fdf9-9388-41d4-bc44-e7abb079d962" />

## Section Structure Overview

### Core Foundations
- **Protocols-Overview.md**  
  Big-picture understanding of protocols and how SOC analysts investigate them.

- **TCP-vs-UDP.md**  
  Transport-layer behavior and how attackers abuse each protocol.

- **Common-Ports.md**  
  Fast SOC reference for ports, services, and suspicious patterns.

---

### Application Layer
Protocols most commonly abused by attackers:
- **HTTP-HTTPS.md** – Web traffic, C2, and exfiltration
- **DNS.md** – Resolution, tunneling, and beaconing
- **FTP-SFTP.md** – File transfer and data exfiltration
- **SMTP-POP3-IMAP.md** – Email delivery, phishing, and abuse

---

### Transport Layer
Low-level behavior that reveals scans and sessions:
- **TCP.md** – Handshakes, sessions, and reliability
- **UDP.md** – Connectionless traffic and covert abuse

---

### Network Layer
Routing and reachability analysis:
- **IP.md** – Addressing, routing, and anomalies
- **ICMP.md** – Reconnaissance and misuse

---

### Security Protocols
Encrypted and secure communications:
- **TLS-SSL.md** – Encryption, certificates, and metadata analysis
- **SSH.md** – Secure access and brute-force detection
- **VPN-Protocols.md** – Tunneling and remote access

---

### Logs and Detection
Where protocol behavior appears in SOC tools:
- **Protocols-In-Logs.md** – How protocols show up in logs
- **Abnormal-Protocol-Behavior.md** – Detecting anomalies

---

### SOC Scenarios (Hands-On)
Realistic investigation cases:
- **Case-01-DNS-Tunneling.md**
- **Case-02-HTTP-C2.md**
- **Case-03-ICMP-Abuse.md**

Each case includes:
- Detection context
- Protocol behavior analysis
- SOC investigation steps
- Practical analyst decision-making

---

## SOC Mindset
Protocols are not memorized — they are **observed**.

SOC analysts focus on:
- Behavior patterns
- Frequency and timing
- Destinations and context
- Correlation across logs and tools

---

## Key Takeaway
Strong protocol knowledge allows SOC analysts to:
- Reduce false positives
- Detect stealthy attacks
- Investigate incidents faster
- Build higher-quality detections
