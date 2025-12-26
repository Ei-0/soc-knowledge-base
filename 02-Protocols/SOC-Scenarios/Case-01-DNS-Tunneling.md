# Case 01 – DNS Tunneling (SOC Investigation Scenario)

DNS is often allowed outbound without strict inspection.  
Attackers abuse this trust to tunnel data and maintain stealthy command-and-control (C2) communication.

This scenario walks through a realistic SOC investigation of DNS tunneling activity.

---

## Detection Context
The SOC receives an alert indicating:
- Abnormally high DNS query volume
- Long and random-looking subdomains
- Repeated DNS requests at regular intervals

Alert source:
- SIEM (DNS analytics rule)

---

## Initial Alert Indicators
- Source host: User workstation
- Destination: External domain
- Query type: A and TXT
- Query frequency: High and periodic
- Domain age: Newly registered

---

## Step 1: Triage
SOC analyst actions:
- Identify the affected host and user
- Validate alert severity
- Confirm DNS traffic is not business-related
- Check if other hosts show similar behavior

Key question:
Is this automated behavior or legitimate application traffic?

---

## Step 2: DNS Log Analysis
Findings:
- Subdomains contain high-entropy strings
- Consistent query intervals (beaconing pattern)
- Repeated NXDOMAIN responses
- TXT records used unusually

Conclusion:
Behavior does not match normal DNS usage.

---

## Step 3: Pivot to Other Logs

### Proxy / Firewall Logs
- No corresponding HTTP traffic to the same domain
- DNS traffic allowed outbound

### Endpoint / EDR Telemetry
- DNS queries initiated by an unknown process
- Process executed from user profile directory

---

## Step 4: Threat Validation
Indicators strongly suggest:
- DNS tunneling
- Covert C2 communication
- Potential data exfiltration

MITRE ATT&CK Mapping:
- Command and Control – Application Layer Protocol: DNS
- Exfiltration – Exfiltration Over Alternative Protocol

---

## Step 5: Containment
SOC response actions:
- Block the malicious domain
- Isolate the affected endpoint
- Terminate malicious process
- Collect forensic artifacts

---

## Step 6: Hunting & Scope Expansion
- Search for same domain across environment
- Identify other hosts with similar DNS patterns
- Review historical DNS logs
- Check for related malware indicators

---

## Lessons Learned
- DNS tunneling can bypass traditional controls
- Behavioral detection is critical
- Correlation between DNS and endpoint data is essential

---

## Key Takeaway
DNS should be monitored not just for domains,  
but for **patterns, frequency, and entropy**.
