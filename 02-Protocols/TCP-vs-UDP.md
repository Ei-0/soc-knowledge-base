# TCP vs UDP (SOC Analyst Perspective)

Understanding the difference between TCP and UDP is critical for SOC analysts, as many attacks, scans, and malware behaviors rely on specific transport-layer characteristics.
<img width="1904" height="1300" alt="image" src="https://github.com/user-attachments/assets/40c4dfeb-f74e-4194-8623-c0fad8be74aa" />

---

## Transport Layer Overview
The transport layer is responsible for:
- Delivering data between hosts
- Managing sessions and ports
- Controlling reliability and flow

The two primary transport protocols are **TCP** and **UDP**.

---

## TCP (Transmission Control Protocol)
<img width="960" height="720" alt="image" src="https://github.com/user-attachments/assets/c99a038c-4a0c-4139-8cf0-6f9db43b6169" />

### Key Characteristics
- Connection-oriented
- Reliable delivery
- Ordered packets
- Error checking and retransmission
- Uses a three-way handshake

### Common Legitimate Uses
- HTTP / HTTPS
- SMTP / IMAP / POP3
- FTP
- SSH
- SMB
- RDP

### SOC Visibility
TCP provides strong visibility due to:
- Handshakes (SYN, SYN-ACK, ACK)
- Session duration
- Retransmissions and resets
- Clear connection states

SOC evidence sources:
- Firewall logs
- IDS/IPS alerts
- Proxy logs
- PCAP analysis

---

## UDP (User Datagram Protocol)

### Key Characteristics
- Connectionless
- No handshake
- No guaranteed delivery
- Faster and lightweight
- Minimal overhead

### Common Legitimate Uses
- DNS
- DHCP
- NTP
- SNMP
- VoIP / streaming
- Some VPN protocols

### SOC Challenges
UDP is harder to analyze because:
- No session state
- Packet loss is normal
- Spoofing is easier
- Behavior often appears noisy

SOC evidence sources:
- NetFlow / sFlow
- Firewall logs
- IDS/IPS alerts
- PCAP analysis

---

## TCP vs UDP (SOC Comparison)

| Feature | TCP | UDP |
|------|-----|-----|
| Connection setup | Yes (Handshake) | No |
| Reliability | Guaranteed | Best-effort |
| Ordering | Yes | No |
| Speed | Slower | Faster |
| Logging clarity | High | Lower |
| Abuse difficulty | Harder | Easier |

---

## Common SOC Detection Scenarios

### TCP-Based Threats
- Port scanning (SYN scans, connect scans)
- Brute-force attacks (SSH, RDP)
- C2 communication over HTTP/HTTPS
- Data exfiltration via web protocols
- Lateral movement using SMB/RDP

Indicators:
- Many SYN packets without completion
- Repeated failed connections
- Long-lived suspicious sessions

---

### UDP-Based Threats
- DNS tunneling
- Reflection and amplification attacks
- Malware beaconing via DNS or custom UDP
- NTP or SNMP abuse
- Covert channels

Indicators:
- High packet rates
- Unusual destination ports
- Abnormal payload sizes
- Repetitive query patterns

---

## SOC Investigation Tips
When analyzing TCP or UDP traffic:
1. Identify the protocol and port
2. Determine if the service is expected on that host
3. Check frequency and timing patterns
4. Correlate with DNS, proxy, and EDR data
5. Validate against known baselines

---

## Practice Mapping
Used heavily in:
- Firewall log analysis
- IDS/IPS triage
- Network traffic analysis
- Threat hunting
- Detection rule tuning

---

## Key Takeaway
TCP gives SOC analysts structure and clarity.  
UDP requires pattern recognition and strong baselines.

Both are essential to understand for accurate detection and investigation.
