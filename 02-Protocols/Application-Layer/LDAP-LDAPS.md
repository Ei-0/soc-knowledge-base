# LDAP & LDAPS (SOC Analyst Perspective)

LDAP is used for directory services and authentication, especially within Active Directory environments.  
It is frequently abused for reconnaissance and privilege escalation.

---

## What This Protocol Does
LDAP allows systems to query directory services.

Common ports:
- TCP 389 (LDAP)
- TCP 636 (LDAPS)

Used for:
- User authentication
- Group membership queries
- Directory lookups

---

## Normal Behavior
Typical LDAP behavior includes:
- Queries from domain-joined systems
- Communication with domain controllers
- Predictable query volumes
- Authenticated access

---

## SOC Visibility
SOC analysts observe LDAP through:
- Domain controller logs
- EDR telemetry
- Network traffic analysis
- SIEM alerts

Common indicators:
- Query volume
- Source host
- Authentication success or failure
- Accessed directory objects

---

## Common Abuse Patterns

### Active Directory Enumeration
Indicators:
- High volume of LDAP queries
- Queries for sensitive groups
- Enumeration from user endpoints

---

### Credential Abuse
Indicators:
- Anonymous or failed LDAP binds
- LDAP queries after credential theft
- Use of LDAP where LDAPS is expected

---

## Indicators of Suspicious LDAP Activity
- LDAP queries from non-domain systems
- Enumeration outside business hours
- Sudden spikes in directory queries

---
<img width="1202" height="629" alt="image" src="https://github.com/user-attachments/assets/538d331f-e7cb-49a2-886c-65e6e355a2e6" />

## SOC Investigation Tips
1. Identify querying host and user
2. Review query frequency and scope
3. Validate against baseline behavior
4. Correlate with authentication events
5. Investigate potential privilege escalation

---

## Practice Mapping
Used during:
- Active Directory attack detection
- Privilege escalation investigations
- Threat hunting
- Incident response

---

## Key Takeaway
Unusual LDAP activity often signals **reconnaissance before escalation**.
