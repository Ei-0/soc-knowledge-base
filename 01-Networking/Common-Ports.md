# Common Network Ports

This document lists the most common TCP and UDP ports that every SOC Analyst
must recognize instantly. Understanding ports helps identify services,
detect anomalies, and investigate attacks efficiently.

---

## 1. What is a Network Port?
A network port is a logical communication endpoint used by applications
to exchange data over a network.

- IP Address → Identifies the device
- Port Number → Identifies the service

Example:
192.168.1.10:443 → HTTPS service on a host

---
<img width="1354" height="780" alt="image" src="https://github.com/user-attachments/assets/9b64d953-3792-4b1d-93cc-d2bbb2a4e373" />

## 2. Port Number Ranges

Range | Name | Description
----- | ---- | -----------
0–1023 | Well-Known Ports | Standard services
1024–49151 | Registered Ports | Vendor applications
49152–65535 | Dynamic / Ephemeral | Temporary client ports

**SOC Tip:**  
Suspicious activity often hides in non-standard ports.

---

## 3. Common TCP Ports

Port | Service | Description | SOC Risk
---- | ------- | ----------- | --------
20/21 | FTP | File Transfer Protocol | Cleartext credentials
22 | SSH | Secure Shell | Brute force, lateral movement
23 | Telnet | Remote access (insecure) | Credential sniffing
25 | SMTP | Email transfer | Phishing, spam
80 | HTTP | Web traffic | Malware delivery
443 | HTTPS | Encrypted web traffic | C2, data exfiltration
445 | SMB | File sharing | Ransomware, lateral movement
3389 | RDP | Remote Desktop | Credential abuse
3306 | MySQL | Database service | Data theft
5985/5986 | WinRM | Windows remote management | Lateral movement

---

## 4. Common UDP Ports

Port | Service | Description | SOC Risk
---- | ------- | ----------- | --------
53 | DNS | Name resolution | DNS tunneling
67/68 | DHCP | IP assignment | Rogue DHCP
69 | TFTP | File transfer | Malware delivery
123 | NTP | Time synchronization | Amplification attacks
161 | SNMP | Network monitoring | Information disclosure
500 | ISAKMP | VPN key exchange | VPN attacks

---

## 5. High-Risk Ports for SOC Monitoring
<img width="600" height="776" alt="image" src="https://github.com/user-attachments/assets/da1e56de-03da-486b-afdf-ee99404c30a2" />

Port | Reason
---- | ------
22 | Frequent brute-force attempts
445 | Common ransomware target
3389 | Exposed RDP = critical risk
53 | DNS tunneling abuse
123 | DDoS amplification
5985 | Living-off-the-Land attacks

---

## 6. Non-Standard Port Usage
Attackers often run services on unusual ports to evade detection.

Examples:
- HTTP on port 8080 or 8443
- SSH on port 2222
- Malware C2 on random high ports

**SOC Rule:**  
Always check **service vs port mismatch**.

---

## 7. Port Scanning Indicators
<img width="1080" height="1080" alt="image" src="https://github.com/user-attachments/assets/73064126-e2ff-4f0e-816f-6dd0a5884420" />

Common scanning behaviors:
- Sequential port access
- Multiple ports from same source
- Short connection attempts
- SYN packets without completion

**SOC Logs to Check:**
- Firewall logs
- IDS/IPS alerts
- NetFlow data

---

## 8. Ports and Lateral Movement
Ports commonly abused for lateral movement:
- 445 (SMB)
- 3389 (RDP)
- 22 (SSH)
- 5985/5986 (WinRM)

Unexpected internal usage of these ports = red flag.

---

## 9. Ports in Incident Response

Incident Type | Ports to Check
------------- | --------------
Phishing | 80, 443
Ransomware | 445, 5985, 3389
C2 Communication | 443, random high ports
Data Exfiltration | 443, 21, 22
Reconnaissance | Multiple ports

---

## 10. Common SOC Mistakes
❌ Assuming HTTPS traffic is safe  
❌ Ignoring high ports  
❌ Focusing only on destination IP  

✅ Always analyze:
- Port
- Protocol
- Direction
- Frequency
- Context

---

## 11. Summary
Understanding ports allows SOC Analysts to:
- Identify services quickly
- Detect abnormal behavior
- Investigate incidents efficiently

> **If you recognize the port, you recognize the attack.**
