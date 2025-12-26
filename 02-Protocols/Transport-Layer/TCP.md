# TCP (Transmission Control Protocol) – SOC Analyst Perspective

TCP is a connection-oriented transport protocol that provides reliable, ordered delivery of data.  
Its structured behavior gives SOC analysts strong visibility into sessions and attacks.

<img width="960" height="720" alt="image" src="https://github.com/user-attachments/assets/5dc1851b-ade2-46ce-b198-a91449726bb6" />

---

## What This Protocol Does
TCP is responsible for:
- Establishing connections
- Ensuring reliable data delivery
- Handling retransmissions and errors
- Managing session states

<img width="1460" height="730" alt="image" src="https://github.com/user-attachments/assets/59310a2f-de10-44bc-97f4-ab92cb44299c" />

Commonly used by:
- HTTP / HTTPS
- SMTP
- FTP
- SSH
- SMB
- RDP

---

## Normal TCP Behavior
Typical TCP behavior includes:
- Three-way handshake (SYN, SYN-ACK, ACK)
- Predictable session duration
- Graceful connection termination (FIN)
- Low retransmission rates

---

## SOC Visibility
SOC analysts observe TCP through:
- Firewall logs
- IDS/IPS alerts
- NetFlow data
- Packet captures (PCAP)

Key TCP indicators:
- SYN, ACK, FIN, RST flags
- Session duration
- Retransmissions
- Connection success or failure

---

## Common Abuse Patterns

### Port Scanning
Indicators:
- Many SYN packets to different ports
- No completed handshakes
- Short-lived connections

---

### Brute-Force Attacks
Indicators:
- Repeated connection attempts
- Many failed sessions
- Consistent source IPs

---

### Command and Control (C2)
Indicators:
- Long-lived TCP sessions
- Periodic beaconing
- Low data volume with high frequency

---

## Indicators of Suspicious TCP Activity
- Excessive SYN packets
- Repeated connection resets
- Unexpected outbound TCP services
- Connections to rare or foreign destinations

---

## SOC Investigation Tips
1. Review handshake completion
2. Analyze session duration and timing
3. Identify source and destination roles
4. Correlate with application-layer logs
5. Compare against baseline behavior

---

## Practice Mapping
Used during:
- Firewall alert triage
- IDS/IPS investigations
- Network traffic analysis
- Threat hunting

---

## Key Takeaway
TCP’s structured nature makes it one of the **most valuable protocols for SOC detection**.
