# Case 02 – HTTP Command and Control (C2)

Attackers frequently use HTTP and HTTPS for command-and-control communication
because this traffic blends in with normal web activity.

This scenario demonstrates how a SOC analyst investigates suspicious HTTP-based C2 traffic.

---

## Detection Context
The SOC receives an alert indicating:
- Repetitive outbound HTTP requests
- Communication with an unknown external domain
- Consistent timing between requests

Alert source:
- Proxy / SIEM behavioral detection rule

---

## Initial Alert Indicators
- Source host: User workstation
- Destination domain: Rare, low-reputation domain
- Protocol: HTTP
- Method: GET
- Frequency: Every 5 minutes
- User-Agent: Non-browser string

---

## Step 1: Triage
SOC analyst actions:
- Identify the affected host and user
- Review alert confidence and severity
- Check if the destination domain is business-related
- Determine if traffic pattern is automated

Key question:
Does this HTTP traffic resemble normal browsing behavior?

---

## Step 2: HTTP Log Analysis
Findings:
- Repeated requests to the same URI path
- Minimal response size
- Consistent request intervals
- User-Agent does not match known browsers

Conclusion:
Traffic shows classic beaconing behavior.

---

## Step 3: DNS and Reputation Check
- Domain is newly registered
- No known business association
- No other legitimate services using this domain

This increases suspicion of malicious activity.

---

## Step 4: Endpoint Correlation
EDR findings:
- HTTP requests initiated by an unknown executable
- Process located in user directory
- No digital signature

This confirms malware-driven communication.

---

## Step 5: Threat Validation
Indicators strongly suggest:
- HTTP-based command and control
- Malware beaconing
- Potential secondary payload delivery

MITRE ATT&CK Mapping:
- Command and Control – Application Layer Protocol: Web
- Ingress Tool Transfer

---

## Step 6: Containment
SOC response actions:
- Block the domain and IP
- Isolate the affected endpoint
- Kill malicious process
- Collect malware sample for analysis

---

## Step 7: Hunting & Scope Expansion
- Search proxy logs for same domain
- Identify other hosts with similar user-agent
- Review historical traffic patterns
- Check for HTTPS variants of the same behavior

---

## Lessons Learned
- C2 traffic often mimics legitimate web traffic
- Timing and repetition are key detection signals
- User-Agent analysis is highly valuable

---

## Key Takeaway
When HTTP traffic is **too regular**,  
it is rarely human.
