# Network Logs

Network logs provide visibility into how devices communicate across a network.
For SOC Analysts, network logs are critical for detecting attacks, investigating
incidents, and understanding attacker behavior.

---

## 1. Why Network Logs Matter in SOC
Almost every cyber attack generates network activity.
Even fileless attacks rely on network communication for:
- Initial access
- Command and Control (C2)
- Lateral movement
- Data exfiltration

> **SOC Principle:**  
> If it communicates, it can be logged.

---

## 2. Common Types of Network Logs

### 2.1 Firewall Logs
<img width="1400" height="1010" alt="image" src="https://github.com/user-attachments/assets/b5c52452-b206-4109-88c3-ec8a39a6c56a" />

#### Description
Firewall logs record traffic that is allowed or blocked based on security rules.

#### Typical Fields
- Source IP
- Destination IP
- Source Port
- Destination Port
- Protocol
- Action (Allow / Block)
- Timestamp

#### SOC Use Cases
- Detect port scanning
- Identify unauthorized outbound traffic
- Investigate blocked attacks

#### Example Indicator
- Internal host repeatedly blocked while trying to access multiple ports

---

### 2.2 Proxy Logs
<img width="1632" height="604" alt="image" src="https://github.com/user-attachments/assets/8a347e71-d66f-4481-adcb-fd517b4d952c" />

#### Description
Proxy logs capture web traffic passing through a proxy server.

#### Typical Fields
- User
- Source IP
- Destination URL
- HTTP method
- Response code
- Bytes transferred

#### SOC Use Cases
- Detect malicious downloads
- Identify access to phishing or C2 domains
- Monitor policy violations

#### Example Indicator
- User accessing newly registered or suspicious domains

---

### 2.3 DNS Logs
<img width="1000" height="746" alt="image" src="https://github.com/user-attachments/assets/4cae41a9-ceac-4347-b37a-9e037e02b061" />

#### Description
DNS logs record domain name resolution requests.

#### Typical Fields
- Source IP
- Queried domain
- Record type
- Response IP
- Timestamp

#### SOC Use Cases
- Detect DNS tunneling
- Identify malware beaconing
- Discover communication with malicious domains

#### Example Indicator
- Long, random-looking domain names
- High-frequency DNS queries

---

### 2.4 IDS / IPS Logs
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/3ee6cb72-958b-4168-b43d-2e62703e1e66" />

#### Description
Intrusion Detection/Prevention Systems generate alerts for suspicious traffic.

#### Typical Fields
- Alert signature
- Severity
- Source/Destination IP
- Protocol
- Payload information

#### SOC Use Cases
- Detect known exploits
- Identify scanning or brute-force attempts
- Confirm active attacks

#### Example Indicator
- Repeated exploit attempts from a single source

---

### 2.5 NetFlow / Flow Logs
<img width="1024" height="640" alt="image" src="https://github.com/user-attachments/assets/00ca266c-b05d-4d31-b75e-1228849e9cb3" />
<img width="1332" height="866" alt="image" src="https://github.com/user-attachments/assets/d7807d1d-e194-41bb-bcc5-e899b686f159" />

#### Description
Flow logs summarize network traffic without capturing payloads.

#### Typical Fields
- Source/Destination IP
- Ports
- Protocol
- Bytes sent/received
- Duration

#### SOC Use Cases
- Detect data exfiltration
- Identify lateral movement
- Monitor traffic patterns

#### Example Indicator
- Large outbound data transfers outside business hours

---

### 2.6 VPN Logs
<img width="500" height="274" alt="image" src="https://github.com/user-attachments/assets/3142631b-2701-4c73-b545-f298d85fc8b6" />

#### Description
VPN logs record remote access activity.

#### Typical Fields
- Username
- Source IP
- Login time
- Logout time
- Authentication result

#### SOC Use Cases
- Detect suspicious remote logins
- Identify compromised credentials
- Investigate access from unusual locations

#### Example Indicator
- Successful login from unexpected country

---

### 2.7 Wireless Network Logs

#### Description
Wireless logs capture Wi-Fi authentication and access events.

#### SOC Use Cases
- Detect rogue access points
- Identify unauthorized devices
- Investigate wireless attacks

---

## 3. Network Logs and Attack Detection

Attack Type | Key Logs
----------- | --------
Phishing | Proxy, DNS
Malware Infection | DNS, Firewall
C2 Communication | DNS, Proxy, NetFlow
Lateral Movement | Firewall, NetFlow
Data Exfiltration | NetFlow, Proxy
DDoS | Firewall, IDS/IPS

---

## 4. Correlating Network Logs
Effective SOC analysis requires correlating multiple log sources:

Example:
- Proxy log shows suspicious domain
- DNS log confirms repeated lookups
- Firewall log shows outbound connections

➡ This correlation strengthens detection confidence.

---

## 5. Common SOC Mistakes with Network Logs
❌ Analyzing logs in isolation  
❌ Ignoring internal traffic  
❌ Trusting encrypted traffic blindly  

✅ Always correlate logs and analyze behavior patterns.

---

## 6. Network Logs in Incident Response

During an incident:
1. Identify affected host
2. Review outbound connections
3. Analyze DNS queries
4. Check lateral movement
5. Confirm data exfiltration

---

## 7. Summary
Network logs are the backbone of SOC visibility.
A skilled SOC Analyst can reconstruct an entire attack timeline
by analyzing network logs effectively.

> **Logs tell the story — the SOC Analyst connects the dots.**
