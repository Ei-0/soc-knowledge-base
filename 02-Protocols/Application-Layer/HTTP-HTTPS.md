# HTTP & HTTPS (SOC Analyst Perspective)

HTTP and HTTPS are the most commonly observed application-layer protocols in SOC environments.  
They are heavily abused by attackers for command-and-control (C2), data exfiltration, and malware delivery.

---

## What This Protocol Does
- HTTP: Transfers web content in cleartext
- HTTPS: Transfers web content encrypted using TLS

Used for:
- Web browsing
- APIs
- Cloud services
- Software updates

---

## Normal Behavior
Typical HTTP/HTTPS behavior includes:
- Requests to known domains (CDNs, SaaS providers)
- Standard HTTP methods (GET, POST)
- Consistent user-agent strings
- Predictable request patterns
- TLS connections with valid certificates

---

## SOC Visibility
SOC analysts typically observe HTTP/HTTPS through:
- Web proxy logs
- Firewall logs
- IDS/IPS alerts
- EDR network telemetry
- Packet captures (limited visibility for HTTPS)

Common fields:
- Source/Destination IP
- Domain / Host header
- URL / URI
- HTTP method
- Response codes
- User-Agent
- TLS SNI / certificate metadata (HTTPS)

---

## Common Abuse Patterns

### Command and Control (C2)
- Periodic beaconing to external servers
- Repeated requests to the same URI
- Low data volume but high frequency
- Non-browser user agents

### Data Exfiltration
- Large outbound POST requests
- Uploads to unknown domains
- Long sessions with high outbound data

### Malware Delivery
- Downloads from newly registered domains
- Suspicious file extensions
- Abnormal response sizes

---

## Indicators of Suspicious HTTP/HTTPS Traffic
- Rare or unknown domains
- Newly registered domains
- Unusual user-agent strings
- Random or encoded URI paths
- Regular time-based request intervals
- TLS connections with uncommon certificates or SNI mismatches

---

## SOC Investigation Tips
1. Validate the destination domain reputation
2. Check frequency and timing of requests
3. Analyze user-agent consistency
4. Pivot to DNS logs for domain history
5. Correlate with endpoint process data (EDR)
6. Compare traffic against known baselines

---

## Practice Mapping
Commonly used during:
- Web proxy alert triage
- IDS/IPS investigation
- Malware analysis
- Threat hunting
- Detection rule tuning

---

## Key Takeaway
HTTP and HTTPS traffic is everywhere.  
Effective SOC detection focuses on **behavior**, not content.
