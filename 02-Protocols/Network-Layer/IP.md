# IP (Internet Protocol) – SOC Analyst Perspective

IP is the foundation of network communication.  
It handles addressing and routing of packets between systems and networks.

<img width="801" height="401" alt="image" src="https://github.com/user-attachments/assets/ce6c1531-db61-4427-9e4c-10050adff70c" />

Every SOC investigation involves IP addresses.

---

## What This Protocol Does
IP is responsible for:
- Logical addressing (IPv4 / IPv6)
- Routing packets across networks
- Fragmentation and reassembly

<img width="1088" height="792" alt="image" src="https://github.com/user-attachments/assets/dabd2bfc-4e27-4dd1-84e5-0c2f6b6ee642" />

Used by all higher-layer protocols.

---

## Normal IP Behavior
Typical IP behavior includes:
- Consistent source IP per host
- Predictable internal vs external IP usage
- Normal TTL values
- Expected communication paths

---

## SOC Visibility
SOC analysts observe IP data through:
- Firewall logs
- IDS/IPS alerts
- NetFlow records
- SIEM events
- Packet captures

Key IP fields:
- Source IP
- Destination IP
- Protocol number
- TTL
- Packet size

---

## Common Abuse Patterns

### IP Spoofing
Indicators:
- Impossible source IP addresses
- Traffic claiming to originate from internal ranges
- Asymmetric traffic flows

---

### Suspicious Outbound Connections
Indicators:
- Traffic to rare geolocations
- Connections to newly registered IP ranges
- Unexpected external communication from servers

---

### Fragmentation Abuse
Indicators:
- Excessive IP fragmentation
- Unusual fragment sizes
- Fragmentation used to evade IDS

---

## Indicators of Suspicious IP Activity
- Communication outside normal geographies
- Sudden changes in destination patterns
- High volume of outbound connections
- Traffic bypassing expected gateways

---

## SOC Investigation Tips
1. Identify asset ownership of source IP
2. Check destination reputation and ASN
3. Validate routing paths
4. Look for spoofing indicators
5. Correlate with transport and application layers

---

## Practice Mapping
Used during:
- Firewall investigations
- Network anomaly detection
- Threat hunting
- Incident response

---

## Key Takeaway
IP provides **context and scope** — it tells SOC analysts *who is talking to whom*.
