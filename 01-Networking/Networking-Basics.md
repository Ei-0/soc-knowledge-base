# Networking Basics

This document provides foundational networking knowledge required for a SOC Analyst.
It focuses on how networks operate, how data moves, and how attackers abuse network
communication during cyber attacks.

---

## 1. What is a Network?
A network is a collection of interconnected devices that communicate to exchange data.
These devices can include:

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/10f95460-2ecb-4bc6-8f50-15f3d9a1a20e" />

- End-user devices (workstations, laptops, mobile devices)
- Servers (web, database, authentication servers)
- Network devices (routers, switches, firewalls)
- IoT devices (printers, cameras, sensors)

From a SOC perspective, **almost every security incident leaves a network footprint**.

---

## 2. Why Networking is Critical for SOC Analysts
Most cyber attacks rely heavily on network communication at different stages:

- Initial Access (phishing links, malicious downloads)
- Payload Delivery (HTTP/HTTPS, FTP)
- Command and Control (C2) communication
- Lateral Movement inside the network
- Data Exfiltration to external destinations

A SOC Analyst must be able to identify **normal vs abnormal network behavior**.

---

## 3. Types of Networks

### 3.1 Local Area Network (LAN)
A LAN connects devices within a limited area such as an office or building.

**SOC Relevance:**
- Internal traffic should follow predictable patterns
- Unexpected connections may indicate lateral movement

---

### 3.2 Wide Area Network (WAN)
A WAN connects networks across large geographic areas.

**SOC Relevance:**
- Inter-branch communication is a common attack path
- Compromised branch offices can be pivot points

---

### 3.3 Wireless LAN (WLAN)
Wireless networks allow devices to connect without physical cables.

**SOC Relevance:**
- Susceptible to rogue access points
- Weak encryption and shared passwords increase risk

---

### 3.4 Virtual Private Network (VPN)
VPNs provide encrypted remote access to internal networks.

**SOC Relevance:**
- Monitor VPN authentication logs
- Detect abnormal login locations or times

---

## 4. Client–Server Model
Most enterprise networks follow the client–server architecture:

- Clients request services
- Servers respond to requests

Examples:
- Web browser → Web server
- Email client → Mail server
- Domain-joined PC → Domain Controller

**SOC Insight:**  
Compromised clients often communicate with multiple servers abnormally.

---

## 5. Peer-to-Peer (P2P) Communication
In P2P networks, devices communicate directly without a central server.

**SOC Relevance:**
- Often used by malware for C2 or file sharing
- Harder to detect due to decentralized nature

---

## 6. Data Transmission Concepts

### 6.1 Packets and Frames
- Data is broken into packets for transmission
- Frames operate at the data-link layer

**SOC Relevance:**
- Packet analysis helps detect suspicious payloads

---

### 6.2 Bandwidth
The maximum data transfer rate of a network.

### 6.3 Latency
The delay between sending and receiving data.

### 6.4 Throughput
The actual amount of data transferred successfully.

**SOC Relevance:**  
Sudden spikes in throughput may indicate data exfiltration.

---

## 7. Network Communication Flow
Typical communication flow:

1. Device sends a request
2. Network routes the request
3. Server processes the request
4. Response is sent back

**SOC Insight:**  
Understanding this flow helps detect anomalies in timing and direction.

---

## 8. Internal vs External Traffic
- **Internal Traffic:** Communication within the organization
- **External Traffic:** Communication with the internet

**SOC Relevance:**
- Internal-to-internal traffic is key for detecting lateral movement
- Internal-to-external traffic reveals C2 and exfiltration attempts

---

## 9. North–South vs East–West Traffic
- **North–South:** Traffic entering or leaving the network
- **East–West:** Traffic moving laterally within the network

**SOC Focus:**  
East–West traffic is often overlooked but heavily abused by attackers.

---

## 10. Common Networking Red Flags for SOC
Indicators that may suggest malicious activity:

- Unusual outbound connections
- Repeated failed connection attempts
- Communication with unknown IP addresses
- Large data transfers outside business hours
- Internal systems communicating unexpectedly

---

## 11. Networking Skills Every SOC Analyst Must Have
- Understand basic network architecture
- Identify common network protocols
- Read firewall and proxy logs
- Analyze traffic flow patterns
- Correlate network events with endpoint alerts

---

## 12. Summary
Networking is the backbone of security monitoring.
A SOC Analyst who understands networking can detect attacks earlier,
investigate incidents faster, and reduce organizational risk.

> **Rule of Thumb:**  
> If you understand the network, you understand the attack.
