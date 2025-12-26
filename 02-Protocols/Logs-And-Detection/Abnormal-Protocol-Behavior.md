# Abnormal Protocol Behavior (SOC Analyst Perspective)

Most detections in SOC are not based on exploits, but on **behavioral anomalies**.  
Understanding what is abnormal is more important than memorizing protocol definitions.

---

## What Is Abnormal Behavior?
Abnormal behavior includes:
- Unusual frequency
- Unexpected destinations
- Rare protocol usage
- Deviations from baseline
- Misuse of legitimate protocols

---

## Common Anomalies by Protocol

### DNS
- Long or random subdomains
- High NXDOMAIN rates
- TXT record abuse
- Beaconing patterns

---

### HTTP / HTTPS
- Repetitive periodic requests
- Rare user-agent strings
- Unknown domains
- Large outbound uploads

---

### SMB / RDP
- Lateral movement between endpoints
- Access to admin shares
- Remote access without authorization

---

### LDAP / Kerberos
- Enumeration spikes
- Authentication without logon events
- Abnormal ticket lifetimes

---

### ICMP / UDP
- Unexpected volume
- Large payloads
- Persistent usage

---

## SOC Detection Techniques
SOC teams detect abnormal behavior using:
- Baseline modeling
- Threshold-based alerts
- Frequency analysis
- Correlation rules
- Threat hunting

---

## SOC Investigation Tips
1. Compare activity to historical baseline
2. Identify the initiating host and process
3. Check timing and repetition
4. Validate business justification
5. Escalate when behavior cannot be explained

---

## Practice Mapping
Used during:
- Threat hunting
- Anomaly-based detections
- Advanced SOC investigations
- Detection tuning

---

## Key Takeaway
Attackers hide inside **normal protocols** —  
SOC analysts detect them by finding what doesn’t belong.
