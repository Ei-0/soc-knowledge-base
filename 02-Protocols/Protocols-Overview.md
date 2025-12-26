# Protocols Overview (SOC Analyst Perspective)

Network protocols define how systems communicate. For SOC analysts, protocols matter because almost every detection, alert, and incident investigation is tied to **protocol behavior** in logs or packet captures.

---

## SOC Goal: Normal vs Suspicious Behavior
When analyzing any alert, ask:
- **What protocol is involved?**
- **What is normal for this protocol in our environment?**
- **What is abnormal (volume, destination, timing, fields, errors)?**
- **What evidence exists in logs/pcaps to confirm malicious intent?**

---

## Protocol Layers (Practical SOC View)

### Application Layer (Most visible in attacks)
Common protocols:
- HTTP/HTTPS (web traffic, C2, exfiltration)
- DNS (name resolution, tunneling, beaconing)
- SMTP/IMAP/POP3 (email delivery, phishing)
- FTP/SFTP (file transfer, exfiltration)
- SMB/RDP (lateral movement in Windows environments)

SOC evidence sources:
- Web proxy logs, WAF logs
- DNS logs
- Email gateway logs
- EDR network telemetry
- Packet captures (Wireshark)

---

### Transport Layer (Session + delivery behavior)
- TCP: connection-oriented (handshake, reliable delivery)
- UDP: connectionless (fast, less overhead)

SOC evidence sources:
- Firewall logs (src/dst IP, ports, action)
- IDS/IPS alerts
- NetFlow/sFlow
- PCAP (handshake, retransmissions, resets)

Key SOC ideas:
- TCP handshakes help validate real connections
- UDP is often used for scans, amplification abuse, and some malware protocols

---

### Network Layer (Routing + reachability)
- IP: addressing and routing
- ICMP: diagnostics (ping, unreachable, time exceeded)

SOC evidence sources:
- Firewall logs
- Router logs
- IDS/IPS alerts
- PCAP

Key SOC ideas:
- Unexpected outbound connections to unusual geos/providers
- ICMP abuse (recon, covert signaling, misused payloads)

---

## Ports and Services (SOC Shortcut)
Ports are not “proof,” but they are strong hints.
Examples:
- 80/443: HTTP/HTTPS
- 53: DNS
- 25/587: SMTP
- 22: SSH
- 3389: RDP
- 445: SMB

SOC tip:
Attackers can tunnel protocols over non-standard ports (e.g., HTTPS over 8443, SSH over 2222), so validate using:
- TLS handshake / certificates
- HTTP headers / methods
- DNS query patterns
- JA3/JA4 (if available)
- DPI / IDS signatures (if available)

---

## What “Normal” Looks Like (Baseline)
A strong SOC builds baselines for:
- Top talkers (hosts generating the most traffic)
- Typical destinations (CDNs, SaaS, known vendors)
- Typical DNS query volume per host
- Typical user agent strings / request patterns
- Expected protocols per subnet (server VLAN vs user VLAN)

---

## Common Suspicious Patterns by Protocol

### DNS
- Very long subdomains or high-entropy labels
- High query rate from a single host (beaconing)
- NXDOMAIN spikes
- TXT record abuse
- Rare TLDs or newly registered domains

### HTTP/HTTPS
- Repeated periodic requests (beaconing)
- Unusual user-agent strings
- Requests to suspicious paths (e.g., /gate.php, /update, random strings)
- Large outbound uploads to unknown hosts (exfiltration)
- TLS to unknown hosts with uncommon certificates / SNI mismatches

### TCP/UDP
- Port scanning patterns (many ports, short intervals)
- Many failed connections (SYN without ACK, resets)
- Unusual outbound services from user endpoints (e.g., SMB/RDP outbound)

### ICMP
- Unusual ICMP volume
- ICMP payload anomalies (large or patterned payloads)
- ICMP used between endpoints where it’s not needed

---

## SOC Workflow: How to Investigate a Protocol-Based Alert
1. Confirm scope: src/dst IP, ports, time window, user/host identity
2. Identify protocol behavior: handshake, queries, requests, error patterns
3. Pivot into supporting data:
   - DNS logs → domain history, frequency, other hosts
   - Proxy logs → URLs, user agents, response codes
   - Firewall logs → allowed/blocked, session counts
   - EDR telemetry → process making the connection
4. Validate intent:
   - Is it expected business traffic?
   - Is it malware-like (beaconing/exfiltration/C2)?
5. Contain and hunt:
   - Block domain/IP if confirmed malicious
   - Search for same indicators across environment

---

## Practice Mapping (Where You’ll Use This)
- SIEM investigations (Splunk / Sentinel / QRadar)
- IDS/IPS triage
- Firewall/proxy analysis
- Packet analysis in Wireshark
- Threat hunting (baseline vs anomalies)
- Detection engineering (tuning rules and reducing noise)

---

## Key Takeaway
Understanding protocols is not memorizing definitions—it's recognizing **behavior patterns** and knowing **where evidence lives** in logs and packet data.
