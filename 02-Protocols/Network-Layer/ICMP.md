# ICMP (Internet Control Message Protocol) – SOC Analyst Perspective

ICMP is used for network diagnostics and error reporting.  
Although not designed for data transfer, it is frequently abused by attackers.

<img width="474" height="259" alt="image" src="https://github.com/user-attachments/assets/72aea10c-3388-441c-b703-4750255eb60e" />

---

## What This Protocol Does
ICMP is used for:
- Connectivity testing (ping)
- Error reporting
- Network diagnostics
- Path discovery (traceroute)

---

## Normal ICMP Behavior
Typical ICMP behavior includes:
- Low-volume ping requests
- Short diagnostic bursts
- ICMP mostly internal or controlled
- Minimal payload data

---

## SOC Visibility
SOC analysts observe ICMP through:
- Firewall logs
- IDS/IPS alerts
- NetFlow data
- Packet captures

Key ICMP indicators:
- ICMP type and code
- Packet frequency
- Payload size
- Source and destination IPs

---

## Common Abuse Patterns

### Reconnaissance
Indicators:
- ICMP sweeps across subnets
- Sequential ping activity
- Discovery before attacks

---

### ICMP Tunneling
Indicators:
- Large or patterned payloads
- Regular ICMP intervals
- Data encoded in echo requests/replies

---

### Evasion Techniques
Indicators:
- ICMP traffic bypassing security controls
- ICMP used where blocked protocols exist

---

## Indicators of Suspicious ICMP Activity
- High ICMP volume
- Large ICMP payloads
- ICMP to or from external systems
- Persistent ICMP traffic over time

---

## SOC Investigation Tips
1. Identify source of ICMP traffic
2. Check if ICMP is required for that host
3. Analyze payload size and frequency
4. Correlate with other protocol activity
5. Investigate potential tunneling

---

## Practice Mapping
Used during:
- Network reconnaissance detection
- Covert channel investigations
- Threat hunting
- IDS/IPS analysis

---

## Key Takeaway
ICMP should be **quiet**.  
When it is noisy or persistent, it deserves investigation.
