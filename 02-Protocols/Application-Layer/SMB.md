# SMB (Server Message Block) – SOC Analyst Perspective
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e55cf180-c2bd-4aec-a48c-a8b741597e4f" />

SMB is a core application-layer protocol used in Windows environments for file sharing, printer access, and inter-system communication.  
It is one of the most abused protocols in lateral movement and ransomware attacks.

---

## What This Protocol Does
SMB allows systems to:
- Share files and folders
- Access network printers
- Communicate within Windows domains

Common ports:
- TCP 445 (modern SMB)
- TCP 139 (legacy NetBIOS SMB)

---

## Normal Behavior
Typical SMB behavior includes:
- Internal-only communication
- Traffic between workstations and file servers
- Authentication via Active Directory
- Predictable access patterns during business hours
- Minimal SMB traffic from user endpoints to the internet

---

## SOC Visibility
SOC analysts observe SMB activity through:
- Firewall logs
- Windows event logs
- EDR telemetry
- IDS/IPS alerts
- Network traffic captures

Common indicators:
- Source and destination IPs
- Authentication attempts
- File access events
- Session duration
- Volume of SMB traffic

---

## Common Abuse Patterns

### Lateral Movement
Attackers move between internal systems using SMB.

Indicators:
- SMB connections between workstations
- Access to administrative shares (C$, ADMIN$)
- New SMB sessions after credential compromise

---

### Ransomware Propagation
Many ransomware families spread via SMB.

Indicators:
- Sudden spikes in SMB traffic
- File encryption activity across multiple hosts
- SMB access followed by process execution

---

### Credential Abuse
SMB authentication is abused after credential theft.

Indicators:
- Failed authentication attempts
- SMB logins from unusual hosts
- NTLM authentication where Kerberos is expected

---

## Indicators of Suspicious SMB Activity
- SMB traffic to external IPs
- User endpoints acting as SMB servers
- High-volume file operations in short time
- Access to sensitive shares without justification

---

## SOC Investigation Tips
1. Identify source and destination hosts
2. Validate if SMB communication is expected
3. Review authentication logs
4. Check for lateral movement patterns
5. Correlate with endpoint process execution
6. Investigate for ransomware indicators

---

## Practice Mapping
Commonly used during:
- Lateral movement investigations
- Ransomware response
- Insider threat cases
- Windows domain incident response

---

## Key Takeaway
Unexpected SMB activity is often a **high-severity signal** in SOC investigations.
