# Network-Based Attacks

This document covers common network-based attacks that SOC Analysts must
identify, investigate, and respond to using network logs and traffic analysis.

---

## 1. Why Network Attacks Matter in SOC
Most cyber attacks rely on network communication to:
- Discover targets
- Exploit vulnerabilities
- Move laterally
- Exfiltrate data

Understanding network attacks allows SOC Analysts to detect threats
early in the kill chain.

---

## 2. Port Scanning
<img width="857" height="407" alt="image" src="https://github.com/user-attachments/assets/240ac181-5944-446e-b24e-9079e6b252c6" />

### Description
Attackers scan networks to discover open ports and running services.

### Common Tools
- Nmap
- Masscan

### Indicators
- Sequential port connection attempts
- Multiple ports targeted from a single IP
- Short-lived TCP connections

### Logs to Check
- Firewall logs
- IDS/IPS alerts
- NetFlow data

### SOC Response
- Identify source IP
- Block or rate-limit scanner
- Investigate targeted hosts

---

## 3. Distributed Denial of Service (DDoS)
<img width="5667" height="2834" alt="image" src="https://github.com/user-attachments/assets/9c045236-af7a-46b1-aa96-46be96ed7fb4" />

### Description
An attack that overwhelms systems or networks with excessive traffic.

### Common Types
- SYN Flood
- UDP Flood
- HTTP Flood
- Amplification attacks (DNS, NTP)

### Indicators
- Sudden traffic spikes
- Service unavailability
- High connection counts

### Logs to Check
- Firewall logs
- IDS/IPS alerts
- Traffic monitoring dashboards

### SOC Response
- Activate DDoS mitigation
- Coordinate with ISP
- Apply rate limiting

---

## 4. Man-in-the-Middle (MITM)

### Description
An attacker intercepts communication between two parties.

### Common Techniques
- ARP Spoofing
- Rogue Access Points
- SSL Stripping

### Indicators
- ARP table changes
- Certificate warnings
- Unexpected gateway changes

### Logs to Check
- Switch logs
- ARP tables
- Wireless logs

### SOC Response
- Isolate affected segment
- Block malicious MAC/IP
- Enforce encryption

---

## 5. ARP Spoofing
<img width="1200" height="917" alt="image" src="https://github.com/user-attachments/assets/d91059de-11ff-47d8-aa19-54c9450656a0" />

### Description
Attacker poisons ARP tables to redirect traffic.

### Indicators
- Duplicate IP/MAC mappings
- Frequent ARP replies
- Network instability

### Logs to Check
- Switch logs
- IDS/IPS alerts
- Endpoint ARP cache

### SOC Response
- Enable ARP inspection
- Segment network
- Remove attacker device

---

## 6. DNS Tunneling
<img width="800" height="480" alt="image" src="https://github.com/user-attachments/assets/63e6d524-3a26-49e8-acf5-d6c0309bc27a" />

### Description
Malware abuses DNS queries to tunnel data.

### Indicators
- Long, random domain names
- High-frequency DNS queries
- Unusual record types

### Logs to Check
- DNS logs
- Proxy logs
- Threat intelligence feeds

### SOC Response
- Block malicious domains
- Isolate infected hosts
- Investigate payloads

---

## 7. Command and Control (C2) Communication

### Description
Compromised systems communicate with attacker infrastructure.

### Common Channels
- HTTPS
- DNS
- Cloud services
- Custom TCP/UDP ports

### Indicators
- Periodic beaconing
- Communication to rare domains
- Traffic outside business hours

### Logs to Check
- Proxy logs
- DNS logs
- NetFlow data

### SOC Response
- Block C2 infrastructure
- Isolate host
- Begin incident response

---

## 8. Lateral Movement

### Description
Attackers move between internal systems to expand access.

### Common Protocols
- SMB (445)
- RDP (3389)
- SSH (22)
- WinRM (5985/5986)

### Indicators
- Unusual internal connections
- Access to multiple hosts
- Credential reuse patterns

### Logs to Check
- Firewall logs
- NetFlow data
- Authentication logs

### SOC Response
- Identify compromised accounts
- Restrict lateral access
- Reset credentials

---

## 9. Data Exfiltration

### Description
Unauthorized transfer of sensitive data outside the network.

### Common Channels
- HTTPS uploads
- DNS tunneling
- Cloud storage services
- FTP/SFTP

### Indicators
- Large outbound transfers
- Encrypted traffic spikes
- Transfers outside normal hours

### Logs to Check
- Proxy logs
- NetFlow data
- Firewall logs

### SOC Response
- Block outbound channels
- Preserve evidence
- Notify incident response team

---

## 10. Network Attacks Summary Table

Attack | Key Indicator | Primary Logs
------ | ------------- | ------------
Port Scanning | Multi-port access | Firewall
DDoS | Traffic spike | IDS/Firewall
MITM | ARP anomalies | Switch
DNS Tunneling | Random domains | DNS
C2 | Beaconing | Proxy/DNS
Lateral Movement | Internal spread | Firewall
Exfiltration | Large uploads | NetFlow

---

## 11. SOC Analyst Mindset
❌ Focus on single alert  
✅ Look for patterns across traffic and logs  

> **One alert is noise — multiple correlated signals are an attack.**

---

## 12. Summary
Network-based attacks are the foundation of modern cyber threats.
SOC Analysts who understand these attacks can detect intrusions
early and respond effectively.

> **If you understand network attacks, you control the battlefield.**
