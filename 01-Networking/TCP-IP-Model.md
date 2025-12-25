# TCP/IP Model

The TCP/IP Model is the practical networking model used in real-world networks
and the internet. Unlike the OSI Model, TCP/IP focuses on implementation rather
than theory.

For SOC Analysts, TCP/IP is the model most commonly referenced in:
- Network traffic analysis
- Firewall and IDS logs
- Incident response investigations

---

## 1. Why the TCP/IP Model Matters in SOC
Most security tools, logs, and protocols are designed around TCP/IP.
Understanding this model allows SOC Analysts to:
- Interpret network alerts correctly
- Understand protocol behavior
- Detect abnormal communication patterns

> **SOC Reality:**  
> OSI explains *how networking works*.  
> TCP/IP explains *how networking is actually used*.

---
<img width="850" height="550" alt="image" src="https://github.com/user-attachments/assets/9095dc9e-efdd-4126-910d-a652038ba444" />

## 2. TCP/IP Model Overview

Layer | Name | Description
----- | ---- | -----------
4 | Application | Network services and applications
3 | Transport | Host-to-host communication
2 | Internet | Routing and IP addressing
1 | Network Access | Physical and local network communication

---

## 3. Application Layer

### Description
The Application layer provides network services directly to user applications.

### Common Protocols
- HTTP / HTTPS
- DNS
- FTP
- SMTP / IMAP / POP3
- SMB
- SSH

### Common Attacks
- Phishing
- Web-based attacks
- Malware downloads
- DNS tunneling
- Credential harvesting

### SOC Logs to Analyze
- Web server logs
- Proxy logs
- DNS logs
- Email security logs

### SOC Example
A workstation communicating with a suspicious domain over HTTPS → **Application Layer alert**.

---

## 4. Transport Layer

### Description
The Transport layer controls data delivery between hosts.

### Key Protocols
- TCP (reliable, connection-oriented)
- UDP (fast, connectionless)

### Common Attacks
- SYN Flood
- UDP Flood
- Port scanning
- Connection exhaustion

### SOC Logs to Analyze
- Firewall connection logs
- IDS/IPS alerts
- NetFlow records

### SOC Insight
Unusual port activity or excessive connections often indicate reconnaissance or DoS.

---
<img width="495" height="353" alt="image" src="https://github.com/user-attachments/assets/7083c3b6-f3bd-41da-beb3-9a226bd65745" />

## 5. Internet Layer

### Description
Responsible for logical addressing and routing packets across networks.

### Common Protocols
- IP (IPv4 / IPv6)
- ICMP
- IPSec

### Common Attacks
- IP spoofing
- ICMP tunneling
- Route manipulation
- Network scanning

### SOC Logs to Analyze
- Router logs
- Firewall traffic logs
- Flow data (NetFlow, sFlow)

---

## 6. Network Access Layer

### Description
Handles physical network access and local delivery.

### Technologies
- Ethernet
- ARP
- MAC addressing
- Wi-Fi (802.11)

### Common Attacks
- ARP spoofing
- MAC flooding
- Rogue access points

### SOC Logs to Analyze
- Switch logs
- Wireless controller logs
- NAC logs

---

## 7. TCP/IP vs OSI Model Comparison

OSI Layer | TCP/IP Layer
--------- | ------------
Application | Application
Presentation | Application
Session | Application
Transport | Transport
Network | Internet
Data Link | Network Access
Physical | Network Access

**SOC Tip:**  
When investigating incidents, logs usually reference TCP/IP layers.

---

## 8. TCP/IP in SOC Investigations

Incident | TCP/IP Layer
-------- | ------------
Phishing | Application
DDoS | Transport
C2 Communication | Application
Lateral Movement | Network Access / Internet
Data Exfiltration | Application / Transport

---

## 9. Common SOC Mistakes with TCP/IP
❌ Ignoring protocol behavior  
❌ Focusing only on destination IP  
❌ Missing abnormal port usage  

✅ Always analyze:
- Protocol
- Port
- Direction
- Frequency
- Destination reputation

---

## 10. Summary
The TCP/IP model is the foundation of modern networking and cybersecurity.
SOC Analysts who master TCP/IP can:
- Detect attacks faster
- Investigate incidents accurately
- Understand attacker behavior

> **If OSI is the map, TCP/IP is the road.**
