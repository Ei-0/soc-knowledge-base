# Subnetting

Subnetting is the process of dividing a large network into smaller,
manageable subnetworks. While often seen as a networking topic,
subnetting is extremely important for SOC Analysts.

Understanding subnetting helps identify abnormal communication,
lateral movement, and segmentation weaknesses.
<img width="574" height="820" alt="image" src="https://github.com/user-attachments/assets/d559b15d-10ca-47a5-b4b3-ea133c0d5c57" />

---

## 1. Why Subnetting Matters in SOC
Subnetting allows organizations to:
- Segment networks
- Control access
- Reduce attack surface
- Improve monitoring

For SOC Analysts, subnetting answers critical questions:
- Should these two hosts communicate?
- Is this traffic crossing a security boundary?
- Is lateral movement occurring?

> **SOC Rule:**  
> Traffic between subnets is more suspicious than traffic within a subnet.

---

## 2. IP Address Structure (Quick Review)

An IPv4 address consists of:
- Network portion
- Host portion

Example:
192.168.10.25

Without subnetting:
- All hosts share the same network
With subnetting:
- Hosts are divided into logical groups

---

## 3. What is a Subnet?
A subnet is a logical subdivision of an IP network.

Example:
- 192.168.1.0/24 → One network
- 192.168.1.0/25 → Two subnets

Subnetting creates **boundaries** that attackers must cross.

---

## 4. CIDR Notation

CIDR (Classless Inter-Domain Routing) defines how many bits are used
for the network portion.

Example:
- /24 = 255.255.255.0
- /25 = 255.255.255.128
- /26 = 255.255.255.192

SOC Relevance:
- Appears in firewall rules
- Used in SIEM queries
- Defines access scopes

---

## 5. Common Enterprise Subnets

Subnet | Typical Use
------ | -----------
10.0.0.0/24 | User workstations
10.0.1.0/24 | Servers
10.0.2.0/24 | DMZ
10.0.3.0/24 | Management
10.0.4.0/24 | VPN users

SOC Insight:
Communication between these subnets should be **strictly controlled**.

---

## 6. Subnetting and Network Segmentation

Segmentation separates:
- Users
- Servers
- External-facing systems
- Critical infrastructure

SOC Benefit:
- Limits lateral movement
- Improves attack detection
- Makes alerts more meaningful

> **Flat networks = fast ransomware spread**

---

## 7. Subnetting and Lateral Movement

Attackers often move:
- From user subnet → server subnet
- From one user subnet → another

Indicators in Logs:
- SMB or RDP between subnets
- Authentication attempts across segments
- New traffic paths

Logs to Check:
- Firewall logs
- NetFlow
- Authentication logs

---

## 8. Subnetting in Firewall Rules

Example Rule:
Allow 10.0.0.0/24 → 10.0.1.0/24 on port 443

SOC Perspective:
- Who is allowed?
- Why is this allowed?
- Is this rule abused?

Overly broad rules = blind spots.

---

## 9. Subnet Awareness During Investigations

SOC Investigation Example:
1. Alert: Internal RDP connection
2. Source: 10.0.0.25 (User subnet)
3. Destination: 10.0.1.10 (Server subnet)

➡ This indicates **potential lateral movement**.

Subnet context changes alert severity.

---

## 10. Common SOC Mistakes with Subnetting
❌ Treating all internal IPs as equal  
❌ Ignoring subnet boundaries  
❌ Not understanding CIDR ranges  

✅ Always ask:
- Is this traffic expected across subnets?
- Does this violate segmentation design?

---

## 11. Subnetting Cheat Sheet

CIDR | Hosts
---- | -----
/24 | 254
/25 | 126
/26 | 62
/27 | 30
/28 | 14

<img width="711" height="955" alt="image" src="https://github.com/user-attachments/assets/82baffa9-ed4c-4777-b579-6063457c7d29" />

SOC Tip:
Smaller subnets = better control and visibility.

---

## 12. Summary
Subnetting is not just a networking concept.
For SOC Analysts, it is a powerful tool to:
- Detect lateral movement
- Identify abnormal traffic
- Assess segmentation effectiveness

> **If you understand subnets, you understand the battlefield.**
