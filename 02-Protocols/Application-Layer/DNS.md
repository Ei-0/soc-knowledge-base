# DNS (SOC Analyst Perspective)

DNS is a critical application-layer protocol used to resolve domain names to IP addresses.  
Because DNS traffic is almost always allowed outbound, it is heavily abused by attackers for stealthy communication.

---

## What This Protocol Does
DNS translates human-readable domain names into IP addresses so systems can communicate.

Used for:
- Web browsing
- Email delivery
- Cloud services
- Software updates

---

## Normal DNS Behavior
Typical DNS behavior includes:
- Short, readable domain names
- Queries to known resolvers
- Predictable query frequency
- Mostly A and AAAA record requests
- Low NXDOMAIN response rates

---

## SOC Visibility
SOC analysts observe DNS through:
- DNS server logs
- SIEM logs
- Firewall logs
- EDR network telemetry
- PCAP analysis

Common DNS fields:
- Source IP / hostname
- Queried domain
- Record type (A, AAAA, TXT, MX)
- Response code (NOERROR, NXDOMAIN)
- Query frequency

---

## Common Abuse Patterns

### DNS Tunneling
Attackers encode data into DNS queries or responses to bypass security controls.

Indicators:
- Very long subdomains
- High-entropy (random-looking) labels
- Frequent TXT record usage
- Consistent query intervals

---

### Malware Beaconing
Malware uses DNS to periodically check in with a command server.

Indicators:
- Repeated queries to the same domain
- Regular time-based intervals
- Low data volume but high frequency

---

### Data Exfiltration
Sensitive data is encoded and sent via DNS queries.

Indicators:
- Abnormally large DNS payloads
- Excessive number of queries from a single host
- Rare or newly registered domains

---

## Indicators of Suspicious DNS Traffic
- Long or random-looking subdomains
- High NXDOMAIN response rates
- Rare TLDs
- Newly registered domains
- Unusual record types (TXT, NULL)
- DNS traffic outside normal business hours

---
<img width="1918" height="978" alt="image" src="https://github.com/user-attachments/assets/9f4a1885-9eba-4f0d-83d1-c7f04720c8cb" />

## SOC Investigation Tips
1. Identify the source host and user
2. Analyze query frequency and timing
3. Check domain age and reputation
4. Pivot to proxy or firewall logs
5. Search for similar patterns across other hosts
6. Correlate with endpoint telemetry

---

## Practice Mapping
Commonly used during:
- DNS alert triage
- Threat hunting
- Malware investigations
- Detection rule tuning
- Incident response

---

## Key Takeaway
DNS traffic is low-noise and high-value.  
Abnormal patterns often indicate **early-stage compromise**.
