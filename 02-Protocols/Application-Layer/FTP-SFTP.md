# FTP & SFTP (SOC Analyst Perspective)

FTP and SFTP are application-layer protocols used for file transfer.  
They are commonly abused by attackers for data exfiltration and unauthorized file movement.

---

## What These Protocols Do
- FTP: Transfers files in cleartext
- SFTP: Transfers files securely over SSH
<img width="805" height="446" alt="image" src="https://github.com/user-attachments/assets/13ec2df0-4cb6-407d-a1a8-7bb055bc6cde" />
<img width="1161" height="712" alt="image" src="https://github.com/user-attachments/assets/9cc22e0f-4e49-420d-b99a-187bbd84e8a5" />

Used for:
- File uploads and downloads
- System backups
- Data exchange between systems

---
<img width="980" height="1377" alt="image" src="https://github.com/user-attachments/assets/bad046f8-add2-42f7-8e56-b26b8d81ae7a" />

## Normal Behavior
Typical FTP/SFTP behavior includes:
- Connections to known internal or partner servers
- Limited number of sessions
- Predictable file sizes and transfer times
- Authenticated access
- Usage by servers rather than user endpoints

---

## SOC Visibility
SOC analysts observe FTP/SFTP through:
- Firewall logs
- IDS/IPS alerts
- Server authentication logs
- EDR network telemetry
- PCAP analysis

Common fields:
- Source/Destination IP
- Username
- Authentication success or failure
- Commands (PUT, GET)
- Session duration
- Data volume

---

## Common Abuse Patterns

### Data Exfiltration
Attackers upload stolen data to external FTP/SFTP servers.

Indicators:
- Large outbound file transfers
- Transfers to unknown external servers
- Unusual transfer times (off-hours)
- Repeated upload commands

---

### Unauthorized Access
Attackers abuse weak or compromised credentials.

Indicators:
- Multiple failed login attempts
- Logins from unusual IP addresses
- New usernames accessing FTP/SFTP
- Access from user endpoints

---

## Indicators of Suspicious FTP/SFTP Activity
- FTP usage in environments where it is not required
- External FTP servers not previously seen
- High-volume transfers from user workstations
- Cleartext FTP credentials observed in PCAP
- Sudden increase in SFTP activity

---

## SOC Investigation Tips
1. Identify the source host and its role
2. Validate the destination server legitimacy
3. Review authentication logs
4. Analyze transfer size and frequency
5. Correlate with endpoint process activity
6. Check for related DNS or HTTP activity

---

## Practice Mapping
Commonly used during:
- Data exfiltration investigations
- Insider threat cases
- Malware investigations
- Network monitoring
- Incident response
<img width="3726" height="2422" alt="image" src="https://github.com/user-attachments/assets/dd4b48d7-e600-400d-a8b6-c659d96cad1b" />

---

## Key Takeaway
FTP is high-risk and outdated.  
Unexpected SFTP activity can indicate **data theft or unauthorized access**.
