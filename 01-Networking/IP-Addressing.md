# IP Addressing

IP addressing is a fundamental networking concept that allows devices
to identify and communicate with each other across networks.

For SOC Analysts, understanding IP addressing is critical for:
- Investigating alerts
- Identifying attack sources
- Distinguishing internal vs external activity
- Detecting spoofing and lateral movement

---

## 1. What is an IP Address?
An IP address is a unique identifier assigned to a device on a network.

Example:
192.168.1.25

SOC Context:
Every alert, log, or packet almost always contains a source IP
and a destination IP.

---

## 2. IPv4 vs IPv6

<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/cc8e2bf9-29dd-4f50-b333-ae4cde9f35a9" />

### IPv4
- 32-bit address
- Written in decimal format
- Example: 10.0.0.15

<img width="1077" height="771" alt="image" src="https://github.com/user-attachments/assets/322fd209-d7a3-460b-b370-5d4e56833b85" />

### IPv6
- 128-bit address
- Written in hexadecimal
- Example: 2001:db8::1

SOC Relevance:
- IPv6 traffic is often less monitored
- Attackers may abuse IPv6 to evade detection

---

## 3. Public vs Private IP Addresses

<img width="729" height="768" alt="image" src="https://github.com/user-attachments/assets/469210a5-0094-488b-9a62-cf0d5cede071" />

### Private IP Ranges
- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

Used for internal networks.

### Public IP Addresses
- Routable on the internet
- Assigned by ISPs

SOC Insight:
Internal systems communicating directly with public IPs
must be carefully monitored.

---

## 4. Internal vs External IPs in SOC

### Internal IPs
- Belong to corporate subnets
- Indicate internal activity

### External IPs
- Belong to internet hosts
- Indicate inbound or outbound traffic

SOC Question:
Should this internal host be talking to that external IP?

---

## 5. Static vs Dynamic IP Addresses

### Static IP
- Manually assigned
- Common for servers and infrastructure

### Dynamic IP
- Assigned by DHCP
- Common for user endpoints

SOC Relevance:
Dynamic IPs require correlation with DHCP logs
to identify the actual device or user.

---

## 6. NAT (Network Address Translation)

<img width="589" height="397" alt="image" src="https://github.com/user-attachments/assets/8e2c1083-b930-48e6-890e-9b52acf3d467" />

NAT allows multiple internal devices to share a single public IP.

SOC Impact:
- External logs may show only the public IP
- Internal correlation is required to find the true source

Logs to Check:
- Firewall logs
- NAT translation logs
- DHCP logs

---

## 7. IP Addressing and Attack Detection

Attack Scenario | IP Clue
--------------- | -------
Phishing Callback | Internal → External IP
Lateral Movement | Internal → Internal IP
Scanning | One IP → Many IPs
Spoofing | Invalid or unexpected IP range

---

## 8. IP Spoofing

### Description
Attackers forge source IP addresses to hide their identity
or bypass security controls.

### SOC Indicators
- Impossible IP locations
- Invalid internal IPs seen on external interfaces
- Asymmetric traffic patterns

---

## 9. IP Reputation in SOC

SOC Analysts often evaluate:
- IP reputation
- Geo-location
- ASN ownership

Use Cases:
- Identify known malicious infrastructure
- Prioritize alerts and incidents

---

## 10. Common SOC Mistakes
❌ Treating all IPs equally  
❌ Ignoring private vs public context  
❌ Forgetting NAT and DHCP correlation  

✅ Always analyze IPs in context.

---

## 11. Summary
IP addressing is more than just numbers.
For SOC Analysts, IPs tell a story about:
- Where traffic originates
- Where it is going
- Whether it makes sense

> **Understand the IP, understand the behavior.**
