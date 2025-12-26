# Defensive Network Controls

Defensive Network Controls are mechanisms used to protect networks from attacks,
detect malicious activity, and limit the impact of security incidents.
SOC Analysts must understand how these controls work to investigate alerts
and recommend mitigation actions.

---

## 1. Why Defensive Controls Matter in SOC
Detection without prevention increases risk.
Prevention without visibility creates blind spots.

A strong security posture requires:
- Prevention
- Detection
- Containment
- Visibility

> **SOC Reality:**  
> Every alert exists because a control detected (or failed to block) something.

---

## 2. Firewalls
<img width="674" height="734" alt="image" src="https://github.com/user-attachments/assets/92a8595b-03ea-4c48-a0b4-4e750cb12229" />

### Description
Firewalls control traffic based on predefined rules.

### Types
- Network Firewall
- Host-based Firewall
- Next-Generation Firewall (NGFW)

### SOC Use Cases
- Block unauthorized access
- Monitor inbound and outbound traffic
- Enforce segmentation policies

### Common Issues
- Overly permissive rules
- Lack of outbound filtering
- Rule shadowing

### SOC Insight
Outbound firewall rules are critical for detecting C2 communication.

---

## 3. Intrusion Detection System (IDS)
<img width="1058" height="794" alt="image" src="https://github.com/user-attachments/assets/e659d30d-c78c-491c-8699-6d8ab0c7eb46" />

### Description
IDS monitors network traffic and generates alerts for suspicious activity.

### Characteristics
- Detects attacks
- Does NOT block traffic
- Operates out-of-band

### SOC Use Cases
- Identify reconnaissance
- Detect exploitation attempts
- Provide early warning

### SOC Challenge
High false positives require tuning and correlation.

---

## 4. Intrusion Prevention System (IPS)
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/ee748950-8057-4829-828a-8057308d153f" />

### Description
IPS actively blocks malicious traffic in real time.

### Characteristics
- Detects and blocks attacks
- Inline deployment
- Can stop exploitation instantly

### SOC Use Cases
- Prevent known attacks
- Block malicious payloads
- Protect vulnerable systems

### SOC Risk
Overly aggressive rules may block legitimate traffic.

---

## 5. Network Segmentation
<img width="2042" height="1002" alt="image" src="https://github.com/user-attachments/assets/de5960c7-8983-4cff-be65-23aa452b69c6" />

### Description
Dividing a network into smaller, isolated segments.

### SOC Benefits
- Limits lateral movement
- Reduces attack surface
- Improves incident containment

### Common Segments
- User network
- Server network
- DMZ
- Management network

### SOC Insight
Lack of segmentation is a common root cause in major breaches.

---

## 6. Network Access Control (NAC)
<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/3c17e4eb-cef3-40f4-8000-34b8944284ed" />

### Description
Controls which devices can access the network.

### SOC Use Cases
- Enforce device compliance
- Block unauthorized endpoints
- Detect rogue devices

### Common Signals
- Unknown MAC addresses
- Failed posture checks

---

## 7. Secure Remote Access
<img width="1428" height="1716" alt="image" src="https://github.com/user-attachments/assets/2b849203-e938-409c-aa1f-804c57fd0f6c" />

### Technologies
- VPN
- Zero Trust Network Access (ZTNA)

### SOC Monitoring
- Authentication logs
- Geo-location anomalies
- Concurrent sessions

### SOC Insight
Compromised credentials often appear first in VPN logs.

---

## 8. Zero Trust Architecture
<img width="1042" height="745" alt="image" src="https://github.com/user-attachments/assets/90ee89ca-33d8-49e9-848a-9c3aeb87f7cf" />

### Core Principles
- Never trust, always verify
- Least privilege access
- Continuous authentication

### SOC Role
- Monitor access decisions
- Investigate denied access attempts
- Validate policy effectiveness

---

## 9. Defense in Depth
<img width="800" height="480" alt="image" src="https://github.com/user-attachments/assets/6aeecf8e-890e-4fb7-ad1a-697943b81a9d" />

### Description
Multiple layered controls protect the network.

### Example Layers
- Firewall
- IDS/IPS
- Endpoint Protection
- Network Segmentation
- Logging & Monitoring

### SOC Benefit
If one control fails, another detects or blocks the attack.

---

## 10. Mapping Controls to Attacks

Attack | Defensive Control
------ | -----------------
Port Scanning | Firewall, IDS
DDoS | Firewall, IPS, Rate Limiting
MITM | Segmentation, Encryption
DNS Tunneling | DNS Monitoring, Firewall
C2 Communication | Firewall, Proxy, IDS
Lateral Movement | Segmentation, NAC
Data Exfiltration | DLP, Proxy, Firewall

---

## 11. Common SOC Mistakes
❌ Assuming controls are correctly configured  
❌ Trusting prevention tools blindly  
❌ Ignoring internal network controls  

✅ Always validate:
- Configuration
- Coverage
- Logging

---

## 12. Summary
Defensive network controls are essential for preventing and detecting attacks.
SOC Analysts must understand how these controls function to:
- Interpret alerts correctly
- Investigate incidents efficiently
- Recommend effective mitigation

> **Good detection starts with good controls.**
