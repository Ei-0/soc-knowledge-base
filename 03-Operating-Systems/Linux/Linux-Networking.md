# 🌐 Linux Networking (SOC & DFIR)

## 📌 Overview
Networking is at the heart of most Linux attacks.

From a SOC and DFIR perspective, Linux networking analysis helps answer:
- Where did the attacker connect from?
- What outbound connections exist?
- Is there command-and-control (C2) traffic?
- Is data being exfiltrated?

Most Linux compromises involve **unauthorized inbound access or suspicious outbound traffic**.

---

## 🧱 Linux Networking Basics
Linux networking is built around:
- Network interfaces
- IP addressing
- Ports and protocols
- Routing tables
- Firewall rules

Every network connection is associated with a **process**.

---

## 🔌 Network Interfaces
Interfaces represent network connections.

Common interface names:
- `eth0`, `ens33` – Ethernet
- `wlan0` – Wireless
- `lo` – Loopback
- `docker0` – Docker bridge
- `tun0` – VPN tunnel

### SOC Relevance
- New or unexpected interfaces may indicate VPNs, tunnels, or containers
- Tunnels are often used for stealthy access

---

## 📡 Listening Ports (Inbound Exposure)
Listening ports indicate services accepting connections.

SOC relevance:
- Exposed services increase attack surface
- Unexpected listening ports may indicate backdoors

High-risk indicators:
- Services listening on unusual ports
- Shells or scripting tools bound to ports
- Services listening on all interfaces (`0.0.0.0`)

---

## 🌍 Outbound Connections (Most Important)
Outbound traffic often reveals:
- Reverse shells
- C2 communication
- Data exfiltration

SOC relevance:
- Linux servers often have limited outbound needs
- Any unusual outbound connection deserves scrutiny

High-risk indicators:
- Outbound connections from shells
- Repeated periodic connections (beaconing)
- Connections to rare or suspicious IPs

---

## 🔁 Reverse Shells (Common Pattern)
Attackers frequently use reverse shells to bypass firewalls.

Characteristics:
- Outbound connection from server to attacker
- Shell process attached to socket
- Often uses TCP or HTTP/S

SOC relevance:
- Shells rarely need network access
- Correlate process + network telemetry

---

## 🔍 Network Utilities Abused by Attackers
Common tools:
- `curl`, `wget`
- `nc` (netcat)
- `socat`
- `ssh`
- `python`, `perl` (network libraries)

SOC relevance:
- These tools performing network activity may indicate abuse
- Context matters more than the binary

---

## 🔐 SSH Networking Context
SSH is the most common Linux remote access method.

Attackers abuse SSH for:
- Initial access
- Lateral movement
- Port forwarding
- Tunneling

SOC relevance:
- SSH connections between internal hosts
- SSH sessions with port forwarding enabled

---

## 🧱 Firewall & Filtering (Basic View)
Linux commonly uses:
- `iptables`
- `nftables`
- `ufw`
- Cloud security groups

SOC relevance:
- Sudden firewall changes may indicate attacker activity
- Disabled firewall services are suspicious

---

## 🚨 High-Risk Networking Indicators
Treat these as critical:
- Outbound connections from `/bin/bash`, `/bin/sh`
- Network activity from cron jobs or systemd services
- Connections to IPs with no business justification
- Listening ports created shortly after compromise
- Encrypted traffic from non-network applications

---

## 📊 What SOC Analysts Should Monitor
High-value telemetry:
- Source and destination IPs
- Ports and protocols
- Associated process and PID
- Connection timing and frequency
- Direction (inbound vs outbound)

Correlation is essential: **process + network = truth**.

---

## 🧩 MITRE ATT&CK Mapping
Linux networking abuse maps to:
- Command and Control
- Exfiltration
- Lateral Movement
- Defense Evasion

---

## 🧪 Real-World Networking Example
1. Attacker gains SSH access
2. Launches reverse shell using `bash`
3. Outbound connection established to attacker IP
4. Periodic beaconing observed every 60 seconds
5. Data exfiltration via encrypted channel

Networking telemetry exposes the attacker’s control path.

---

## 🧠 SOC Analyst Mindset
Always ask:
- Should this system initiate outbound connections?
- Does this process normally use the network?
- Is the destination expected?
- Is the timing regular or human-driven?

On Linux, **unexpected outbound traffic is often the biggest red flag**.

---

