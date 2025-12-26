# Network Devices

Network devices form the backbone of enterprise networks.
SOC Analysts must understand how each device works, what traffic it handles,
and what logs it generates.

---

## 1. Router
<img width="755" height="500" alt="image" src="https://github.com/user-attachments/assets/321dc842-ffd0-42da-9c82-d88e4416e0f3" />

### Description
A router connects different networks and routes traffic between them.

### Key Functions
- IP routing
- Network segmentation
- Traffic forwarding

### SOC Logs
- Routing logs
- Traffic flow logs
- Access control logs

### SOC Use Case
- Detect abnormal routing behavior
- Identify traffic between unexpected networks

---

## 2. Switch
<img width="799" height="1109" alt="image" src="https://github.com/user-attachments/assets/91282357-1f57-4115-907b-514a17e9cfc5" />

### Description
A switch connects devices within the same network segment.
<img width="1086" height="300" alt="image" src="https://github.com/user-attachments/assets/7c0aed5d-9e95-4764-9a43-c4de56098453" />

### Key Functions
- MAC address forwarding
- VLAN segmentation

### SOC Logs
- MAC address tables
- Port status logs
- VLAN activity logs

### SOC Use Case
- Detect ARP spoofing
- Identify MAC flooding
- Investigate lateral movement

---

## 3. Firewall
<img width="1000" height="563" alt="image" src="https://github.com/user-attachments/assets/784b3733-304b-4a75-9169-db15583be749" />

### Description
A firewall enforces security rules to allow or block traffic.

### Types
- Network Firewall
- Host-based Firewall
- Next-Generation Firewall (NGFW)

### SOC Logs
- Allowed/Blocked traffic
- Rule matches
- Application control logs

### SOC Use Case
- Detect scanning and brute-force attacks
- Monitor outbound connections

---

## 4. Intrusion Detection System (IDS)

### Description
IDS monitors traffic and generates alerts for suspicious activity.

### Characteristics
- Out-of-band deployment
- Detection only

### SOC Logs
- Alert signatures
- Traffic metadata
- Severity levels

### SOC Use Case
- Early attack detection
- Reconnaissance alerts

---

## 5. Intrusion Prevention System (IPS)

### Description
IPS blocks malicious traffic in real time.

### Characteristics
- Inline deployment
- Detection and prevention

### SOC Logs
- Blocked attacks
- Exploit signatures
- Drop actions

### SOC Use Case
- Prevent exploitation
- Stop malware propagation

---

## 6. Proxy Server

### Description
A proxy acts as an intermediary between users and the internet.

### Key Functions
- Web filtering
- Content inspection
- User attribution

### SOC Logs
- URL access logs
- User activity logs
- Download events

### SOC Use Case
- Detect malicious downloads
- Investigate user web activity

---

## 7. Load Balancer
<img width="1516" height="872" alt="image" src="https://github.com/user-attachments/assets/474ca64c-3f4a-4c3d-ace8-55b01fbc259c" />

### Description
Distributes traffic across multiple servers.

### Key Functions
- Traffic distribution
- High availability

### SOC Logs
- Connection logs
- Health checks
- Backend server mapping

### SOC Use Case
- Identify abnormal traffic patterns
- Detect application-layer attacks

---

## 8. Wireless Controller

### Description
Manages wireless access points.

### SOC Logs
- Authentication events
- Device associations
- Rogue AP alerts

### SOC Use Case
- Detect unauthorized devices
- Investigate wireless attacks

---

## 9. Network Devices Summary

Device | Primary Role | Key SOC Logs
------ | ------------ | -------------
Router | Network routing | Flow logs
Switch | Internal connectivity | MAC/VLAN logs
Firewall | Traffic filtering | Allow/Block logs
IDS | Detection | Alerts
IPS | Prevention | Block logs
Proxy | Web access | URL logs
Load Balancer | Traffic distribution | Connection logs
Wireless Controller | Wi-Fi management | Auth logs

---

## 10. SOC Analyst Mindset
❌ Viewing devices in isolation  
✅ Correlating logs across devices  

> **Each device sees part of the attack — SOC connects the full picture.**

---

## 11. Summary
Understanding network devices allows SOC Analysts to:
- Identify log sources
- Interpret alerts accurately
- Investigate incidents efficiently

> **Know the device, know the log, know the attack.**
