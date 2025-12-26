# RDP (Remote Desktop Protocol) – SOC Analyst Perspective

RDP is used to remotely access Windows systems.  
It is one of the most targeted protocols for brute-force attacks, credential abuse, and lateral movement.
<img width="1200" height="628" alt="image" src="https://github.com/user-attachments/assets/329da79d-745e-4f21-9b92-049e6abdc422" />

---

## What This Protocol Does
RDP enables remote graphical access to Windows systems.

Common port:
- TCP 3389

Used for:
- Remote administration
- IT support
- Server management

---

## Normal Behavior
Typical RDP behavior includes:
- Access from known admin systems
- Limited number of source IPs
- Business-hour usage
- Authenticated domain users
- Short, task-oriented sessions

---

## SOC Visibility
SOC analysts observe RDP through:
- Firewall logs
- Windows security event logs
- EDR telemetry
- IDS/IPS alerts

Common indicators:
- Source and destination IPs
- Login success or failure
- Username
- Session duration
- Logon type

---

## Common Abuse Patterns

### Brute-Force Attacks
Indicators:
- Multiple failed login attempts
- Repeated attempts from the same IP
- Login attempts across many usernames

---

### Lateral Movement
Indicators:
- RDP access between workstations
- New RDP sessions after credential compromise
- RDP access outside admin groups

---

### External Exposure
Indicators:
- RDP exposed to the internet
- Successful logins from foreign IPs
- Sudden RDP usage on endpoints

---

## Indicators of Suspicious RDP Activity
- RDP from user workstations
- Logins outside normal hours
- Multiple failed attempts followed by success
- RDP usage without ticket or change record

---

## SOC Investigation Tips
1. Identify source IP and user
2. Check account privilege level
3. Review failed vs successful logins
4. Correlate with EDR process activity
5. Validate if access was authorized

---

## Practice Mapping
Used during:
- Initial access investigations
- Lateral movement detection
- Incident response
- Brute-force alert triage

---

## Key Takeaway
Unplanned RDP activity should always be treated as **high risk**.
