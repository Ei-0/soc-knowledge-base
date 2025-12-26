# UDP (User Datagram Protocol) – SOC Analyst Perspective

UDP is a connectionless transport protocol focused on speed rather than reliability.  
Its lack of session state makes detection more challenging for SOC analysts.

---

## What This Protocol Does
UDP provides:
- Fast data transmission
- No connection setup
- No delivery guarantees
- Minimal overhead

Commonly used by:
- DNS
- DHCP
- NTP
- SNMP
- VoIP
- Streaming services

---

## Normal UDP Behavior
Typical UDP behavior includes:
- Short bursts of traffic
- Predictable destination services
- Small packet sizes
- No retransmission tracking

---

## SOC Visibility
SOC analysts observe UDP through:
- Firewall logs
- NetFlow / sFlow
- IDS/IPS alerts
- Packet captures

Key UDP indicators:
- Packet rate
- Payload size
- Destination ports
- Traffic frequency

---

## Common Abuse Patterns

### DNS Tunneling
Indicators:
- High query volume
- Large payloads
- Repetitive patterns

---

### Reflection & Amplification Attacks
Indicators:
- Large outbound responses
- Small inbound requests
- Spoofed source IPs

<img width="640" height="411" alt="image" src="https://github.com/user-attachments/assets/22dd4c90-10db-45da-a27d-3f3dc1866050" />

---

### Malware Beaconing
Indicators:
- Regular periodic traffic
- Small packets at fixed intervals
- Unknown destination servers

---

## Indicators of Suspicious UDP Activity
- High packet rates
- Traffic to uncommon ports
- UDP services from user endpoints
- Large payloads where not expected

---

## SOC Investigation Tips
1. Identify expected UDP services
2. Analyze frequency and timing
3. Validate destination legitimacy
4. Correlate with DNS and endpoint data
5. Compare with baseline traffic

---

## Practice Mapping
Used during:
- DDoS detection
- DNS abuse investigations
- Network anomaly detection
- Threat hunting

---

## Key Takeaway
UDP requires **behavior-based detection**, not session tracking.
