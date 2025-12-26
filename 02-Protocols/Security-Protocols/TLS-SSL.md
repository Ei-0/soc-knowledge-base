# TLS / SSL (SOC Analyst Perspective)

TLS (formerly SSL) provides encryption for data in transit.  
While it protects confidentiality, it also enables attackers to hide malicious activity.

<img width="1080" height="1200" alt="image" src="https://github.com/user-attachments/assets/52796a6e-b85a-4980-b9e1-3d545ffbfa3e" />

---

## What This Protocol Does
TLS encrypts application-layer traffic to ensure:
- Confidentiality
- Integrity
- Authentication

Commonly used with:
- HTTPS
- SMTP (STARTTLS)
- FTPS
- IMAPS / POP3S

---

## Normal Behavior
Typical TLS behavior includes:
- Valid certificates issued by trusted CAs
- Known server names (SNI)
- Standard cipher suites
- Reasonable certificate lifetimes

---

## SOC Visibility
SOC analysts observe TLS through:
- Firewall logs
- Proxy logs
- IDS/IPS alerts
- EDR telemetry
- TLS metadata (not payload)

Key TLS indicators:
- Server Name Indication (SNI)
- Certificate issuer and validity
- JA3 / JA4 fingerprints
- Cipher suites
- Session duration

---

## Common Abuse Patterns

### Encrypted Command and Control
Indicators:
- TLS connections to unknown domains
- Periodic beaconing
- Rare JA3 fingerprints

---

### Certificate Abuse
Indicators:
- Self-signed certificates
- Recently issued certificates
- Certificate/SNI mismatch

---

### Domain Fronting
Indicators:
- Mismatch between SNI and destination behavior
- Traffic using CDN IPs with unusual patterns

---

## Indicators of Suspicious TLS Activity
- Connections to newly registered domains
- Rare or unique JA3 fingerprints
- Long-lived encrypted sessions
- TLS from non-browser processes

---

## SOC Investigation Tips
1. Validate certificate issuer and age
2. Check SNI and domain reputation
3. Compare JA3/JA4 against known baselines
4. Correlate with DNS and EDR data
5. Identify originating process

---

## Practice Mapping
Used during:
- Malware C2 investigations
- Encrypted traffic analysis
- Threat hunting
- Detection engineering

---

## Key Takeaway
TLS hides content, not **behavior**.  
SOC detection relies on metadata and patterns.
