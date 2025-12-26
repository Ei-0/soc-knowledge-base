# VPN Protocols (SOC Analyst Perspective)

VPN protocols create encrypted tunnels that allow remote or site-to-site access.  
They are critical for business operations but also a high-value target for attackers.

<img width="850" height="233" alt="image" src="https://github.com/user-attachments/assets/b95960fd-4992-417c-a592-e262d48f2dcf" />

---

## What These Protocols Do
VPNs provide:
- Encrypted network tunnels
- Remote user access
- Site-to-site connectivity

Common VPN protocols:
- IPsec
- OpenVPN
- WireGuard
- SSL VPN

---

## Normal Behavior
Typical VPN behavior includes:
- Connections from known users and locations
- Predictable login times
- Stable session durations
- Known VPN gateways

---

## SOC Visibility
SOC analysts observe VPN activity through:
- VPN gateway logs
- Firewall logs
- Authentication logs
- SIEM alerts

Key VPN indicators:
- User identity
- Source IP and location
- Session duration
- Authentication method

---

## Common Abuse Patterns

### Credential Abuse
Indicators:
- VPN logins from unusual geolocations
- Multiple failed attempts
- New devices accessing VPN

---

### Persistence
Indicators:
- Long-lived VPN sessions
- VPN access outside business hours
- VPN usage after account compromise

---

## Indicators of Suspicious VPN Activity
- VPN access from unexpected countries
- Concurrent sessions from different locations
- Sudden spikes in VPN usage
- Privileged access via VPN

---

## SOC Investigation Tips
1. Validate user identity and role
2. Check source IP reputation
3. Review authentication method (MFA vs password)
4. Correlate with endpoint activity
5. Confirm business justification

---

## Practice Mapping
Used during:
- Remote access investigations
- Account compromise response
- Insider threat detection
- Incident response

---

## Key Takeaway
VPN access equals **network trust** — protect and monitor it aggressively.
