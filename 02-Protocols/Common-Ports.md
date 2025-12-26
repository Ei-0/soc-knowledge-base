# Common Ports (SOC Analyst Reference)

Network ports help SOC analysts quickly identify the likely service or protocol involved in an alert.  
Ports are **indicators**, not proof — attackers frequently use non-standard ports.

---

## Why Ports Matter in SOC
Ports help analysts:
- Identify expected vs unexpected services
- Spot scanning and reconnaissance activity
- Detect lateral movement
- Quickly triage firewall and IDS alerts

---

## Commonly Used Ports

| Port | Protocol | Service | SOC Relevance |
|------|--------|--------|---------------|
| 21 | TCP | FTP | Legacy file transfer, possible data exfiltration |
| 22 | TCP | SSH | Remote access, brute-force attempts |
| 23 | TCP | Telnet | Insecure, often abused if exposed |
| 25 | TCP | SMTP | Email sending, spam, phishing |
| 53 | TCP/UDP | DNS | Tunneling, beaconing, exfiltration |
| 80 | TCP | HTTP | Web traffic, C2 communication |
| 443 | TCP | HTTPS | Encrypted web traffic, hidden C2 |
| 110 | TCP | POP3 | Email retrieval |
| 143 | TCP | IMAP | Email retrieval |
| 3389 | TCP | RDP | Lateral movement, brute-force |
| 445 | TCP | SMB | Lateral movement, ransomware |
| 123 | UDP | NTP | Amplification abuse |
| 161 | UDP | SNMP | Reconnaissance, misconfiguration |
| 5060 | UDP/TCP | SIP | VoIP abuse, scanning |

---

## High-Risk Ports in SOC

| Port | Reason |
|------|-------|
| 21 | Cleartext credentials |
| 23 | No encryption |
| 3389 | High-value target |
| 445 | Worms and ransomware |
| 53 | Easy to tunnel data |
| 80/443 | Most common malware C2 |

---

## Suspicious Port Patterns
Indicators SOC analysts should watch for:
- High number of connection attempts across many ports (port scanning)
- User endpoints hosting server services
- Outbound SMB or RDP connections
- Services running on non-standard ports
- Rare or unused ports with consistent traffic

---

## SOC Investigation Tips
When a port triggers an alert:
1. Identify the host role (user, server, network device)
2. Validate if the port/service is expected
3. Check protocol behavior (not just port number)
4. Correlate with process, user, and DNS data
5. Look for repetition or automation patterns

---

## Practice Mapping
Used in:
- Firewall alert triage
- IDS/IPS analysis
- Threat hunting
- Network baseline creation
- Incident response investigations

---

## Key Takeaway
Ports provide fast context, not final answers.  
Always confirm **service behavior**, not just port numbers.
