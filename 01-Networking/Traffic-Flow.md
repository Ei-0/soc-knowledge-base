# Network Traffic Flow

Understanding network traffic flow is a critical skill for SOC Analysts.
Many attacks are not detected by signatures, but by recognizing
abnormal traffic patterns.

---

## 1. What is Network Traffic Flow?
Network traffic flow describes how data moves:
- Between devices
- Across network segments
- In and out of the organization

Traffic flow answers key SOC questions:
- Who is talking to whom?
- From where to where?
- How often?
- How much data?

---

## 2. Internal vs External Traffic

### Internal Traffic
Communication between devices inside the organization.

Examples:
- Workstation → File Server
- Server → Database
- Domain Controller → Client

SOC Importance:
- Should follow predictable patterns
- Unexpected internal connections often indicate lateral movement

---

### External Traffic
Communication between internal devices and the internet.

Examples:
- User browsing websites
- Software updates
- Cloud services

SOC Importance:
- Main path for C2 communication
- Primary channel for data exfiltration

---

## 3. North–South Traffic
<img width="1024" height="823" alt="image" src="https://github.com/user-attachments/assets/5823f90c-0fc8-46fd-91b7-0f9c7f4fe224" />

### Description
Traffic that enters or leaves the internal network.

Examples:
- Internet → Web Server
- User → External Website

SOC Focus:
- Perimeter defenses
- Firewall and proxy visibility
- External threat detection

Common Threats:
- Malware downloads
- Phishing callbacks
- External scanning

---

## 4. East–West Traffic

### Description
Traffic that moves laterally within the internal network.

Examples:
- Workstation → Workstation
- Server → Server

SOC Focus:
- Detecting lateral movement
- Identifying compromised internal hosts

Common Threats:
- Ransomware spread
- Credential abuse
- Internal reconnaissance

> **SOC Insight:**  
> Most breaches fail at detection because East–West traffic is ignored.

---

## 5. Normal vs Abnormal Traffic

### Normal Traffic Characteristics
- Consistent destinations
- Expected ports and protocols
- Business-hour activity
- Predictable data volume

---

### Abnormal Traffic Indicators
- Rare destinations
- Non-standard ports
- Beaconing patterns
- Large transfers at unusual times

SOC Analysts must establish a **baseline** to detect anomalies.

---

## 6. Beaconing Behavior

### Description
Malware communicates with C2 servers at regular intervals.

Indicators:
- Fixed time intervals
- Small, repeated data transfers
- Long-lived connections

Logs to Analyze:
- DNS logs
- Proxy logs
- NetFlow data

---

## 7. Traffic Flow and Lateral Movement
<img width="1838" height="938" alt="image" src="https://github.com/user-attachments/assets/64ee8346-5eb9-4287-bb4e-ecba14281ed6" />

Common Lateral Movement Paths:
- SMB (445)
- RDP (3389)
- SSH (22)
- WinRM (5985/5986)

Indicators:
- One host connecting to many internal systems
- Authentication attempts across segments
- New internal traffic paths

---

## 8. Traffic Direction Matters

Direction | Example | SOC Meaning
--------- | ------- | -----------
Inbound | Internet → Server | Attack surface
Outbound | Host → Internet | C2 / Exfiltration
Lateral | Host → Host | Compromise spread

---

## 9. Using Traffic Flow in Investigations

SOC Investigation Steps:
1. Identify suspicious host
2. Map its traffic flow
3. Check external destinations
4. Analyze internal connections
5. Correlate with endpoint alerts

Traffic flow helps build the **attack timeline**.

---

## 10. Common SOC Mistakes
❌ Focusing only on alerts  
❌ Ignoring internal traffic  
❌ Not establishing baselines  

✅ Always analyze traffic patterns, not single events.

---

## 11. Summary
Traffic flow analysis allows SOC Analysts to:
- Detect stealthy attacks
- Identify lateral movement
- Discover data exfiltration

> **Alerts show symptoms. Traffic flow reveals the disease.**
