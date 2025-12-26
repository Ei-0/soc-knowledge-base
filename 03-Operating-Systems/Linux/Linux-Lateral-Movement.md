# 🌐 Linux Lateral Movement (SOC & DFIR)

## 📌 Overview
Lateral Movement on Linux is the technique attackers use to **move from one compromised host to others** within the same environment.

From a SOC and DFIR perspective, lateral movement is critical because:
- It turns a single-host compromise into a full-environment breach
- It usually follows credential theft or key abuse
- It often targets servers, databases, and cloud workloads

Stopping lateral movement is often the **last chance** to contain an incident.

---

## 🧱 Why Lateral Movement Works on Linux
Attackers succeed due to:
- Reused credentials or SSH keys
- Over-trusted internal networks
- Weak SSH hardening
- Excessive sudo or root trust
- Poor segmentation in cloud and data centers

Linux environments heavily rely on **SSH and trust relationships**.

---

## 🔑 Common Linux Lateral Movement Techniques

## 1️⃣ SSH Credential Reuse
Attackers reuse:
- Passwords
- SSH private keys
- Agent-forwarded credentials

### SOC Relevance
- Same user authenticating to multiple hosts
- SSH logins from unexpected source hosts
- Sudden expansion of access after initial compromise

---

## 2️⃣ SSH Authorized Keys Abuse
Attackers copy their SSH key to:
- Other user accounts
- Privileged accounts
- Multiple servers

### SOC Relevance
- Identical SSH keys appearing on multiple hosts
- Keys added shortly after compromise
- Root or service accounts receiving new keys

---

## 3️⃣ SSH Agent Forwarding Abuse
If agent forwarding is enabled:
- Attacker can pivot without stealing keys
- Authentication succeeds using forwarded agent

### SOC Relevance
- SSH logins without local private keys
- Lateral movement without new credential artifacts

---

## 4️⃣ Sudo-Based Pivoting
Attackers use sudo rights to:
- Switch users
- Access additional systems
- Extract credentials

### SOC Relevance
- sudo usage followed by outbound SSH
- Privileged user sessions spreading across hosts

---

## 5️⃣ Shared Credentials & Configuration Files
Attackers harvest credentials from:
- `.bash_history`
- `.env` files
- Application config files
- Deployment scripts

### SOC Relevance
- SSH access using service or application accounts
- Access patterns inconsistent with application behavior

---

## 6️⃣ NFS and Shared Storage Abuse
If NFS is misconfigured:
- Attackers write files executed on other hosts
- Trust boundaries are bypassed

### SOC Relevance
- Executables appearing simultaneously on multiple hosts
- Persistence spreading via shared paths

---

## 7️⃣ Cloud & Container Lateral Movement
In cloud/Linux environments attackers pivot via:
- Metadata services
- IAM credentials
- Kubernetes service accounts

### SOC Relevance
- Access to cloud APIs from non-management hosts
- New tokens issued after host compromise

---

## 🚨 High-Risk Lateral Movement Indicators
SOC analysts should treat these as critical:
- SSH logins between servers without clear purpose
- One host authenticating to many others rapidly
- Privileged account spread (root/sudo users)
- Identical SSH keys reused across systems
- Access occurring outside normal operational patterns

---

## 📊 What SOC Analysts Should Monitor
High-value telemetry includes:
- SSH authentication logs
- Source and destination host relationships
- User account reuse patterns
- sudo + SSH sequences
- Key and credential propagation

Correlation across hosts is essential.

---

## 🧩 MITRE ATT&CK Mapping
Linux lateral movement maps to:
- Lateral Movement
- Credential Access
- Privilege Escalation

---

## 🧪 Real-World Lateral Movement Example
1. Attacker compromises a public-facing Linux server
2. Harvests SSH keys from the user home directory
3. Authenticates to an internal database server
4. Uses sudo to access additional hosts
5. Expands control across the environment

The breach grows because **trust was assumed**.

---

## 🧠 SOC Analyst Mindset
Always ask:
- Why is this host connecting to that host?
- Is this user supposed to access multiple systems?
- Did lateral movement follow credential access?
- Is this behavior normal for this environment?

Lateral movement reveals **attacker intent and goals**.

---

