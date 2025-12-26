# SSH (Secure Shell) – SOC Analyst Perspective

SSH provides encrypted remote command-line access.  
It is commonly targeted for brute-force attacks and lateral movement.

---

## What This Protocol Does
SSH enables:
- Secure remote administration
- Command execution
- File transfer (SCP / SFTP)

Common port:
- TCP 22


<img width="900" height="560" alt="image" src="https://github.com/user-attachments/assets/3c546a32-5a08-4796-86dd-2a40b00e0c00" />

<img width="920" height="272" alt="image" src="https://github.com/user-attachments/assets/b6a3ef1a-4829-4cf0-839d-c3df7daba270" />

---

## Normal Behavior
Typical SSH behavior includes:
- Access from known admin hosts
- Key-based authentication
- Limited login attempts
- Short, task-focused sessions

---

## SOC Visibility
SOC analysts observe SSH through:
- Firewall logs
- Server authentication logs
- IDS/IPS alerts
- EDR telemetry

Key SSH indicators:
- Authentication success or failure
- Source IP
- Username
- Session duration

<img width="800" height="548" alt="image" src="https://github.com/user-attachments/assets/837ad3d2-2373-4864-8e01-5300ff797d5c" />

---

## Common Abuse Patterns

### Brute-Force Attacks
Indicators:
- Many failed login attempts
- Attempts across multiple usernames
- Access from unknown IPs

---

### Lateral Movement
Indicators:
- SSH between internal systems
- New SSH access paths
- SSH sessions following credential theft

---

## Indicators of Suspicious SSH Activity
- SSH access from user endpoints
- Password-based authentication where keys are expected
- SSH from foreign or rare IP ranges
- Unusual session timing

---

## SOC Investigation Tips
1. Identify source IP and account
2. Review authentication method
3. Correlate with endpoint activity
4. Check for privilege escalation
5. Validate access authorization

---

## Practice Mapping
Used during:
- Server compromise investigations
- Lateral movement detection
- Incident response
- Access monitoring

---

## Key Takeaway
Unexpected SSH access is often a **direct intrusion signal**.
