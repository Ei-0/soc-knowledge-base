# Kerberos (SOC Analyst Perspective)

Kerberos is the primary authentication protocol used in Active Directory environments.  
Attackers abuse Kerberos tickets for stealthy credential-based attacks.

---
<img width="1385" height="779" alt="image" src="https://github.com/user-attachments/assets/0450bc87-7c00-44a8-b8ae-d3b7b531a552" />

## What This Protocol Does
Kerberos uses tickets to authenticate users and services.

Common ports:
- TCP/UDP 88

Used for:
- Domain authentication
- Single sign-on (SSO)

---

## Normal Behavior
Typical Kerberos behavior includes:
- Ticket requests during logon
- Short-lived tickets
- Communication with domain controllers
- Predictable authentication patterns

---

## SOC Visibility
SOC analysts observe Kerberos through:
- Domain controller security logs
- EDR telemetry
- SIEM alerts

Common indicators:
- Ticket request events
- Ticket lifetimes
- Service ticket usage
- Authentication failures

---

## Common Abuse Patterns

### Pass-the-Ticket
Indicators:
- Ticket reuse across systems
- Authentication without interactive logon

---

### Golden / Silver Ticket Attacks
Indicators:
- Long-lived tickets
- Authentication without contacting domain controller
- Privileged access without corresponding logon events

---

## Indicators of Suspicious Kerberos Activity
- Abnormally long ticket lifetimes
- Authentication from unexpected hosts
- Privileged access without prior logon
- Ticket usage outside normal hours

---

## SOC Investigation Tips
1. Review Kerberos-related event IDs
2. Analyze ticket lifetime anomalies
3. Correlate with logon activity
4. Validate account privilege changes
5. Investigate persistence mechanisms

---

## Practice Mapping
Used during:
- Credential abuse investigations
- Advanced persistent threat (APT) detection
- Active Directory incident response

---

## Key Takeaway
Kerberos abuse often indicates a **mature or persistent attacker**.
