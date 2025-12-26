# ☁️ Linux Cloud Security Basics (AWS / GCP) — SOC View

## 📌 Overview
Linux workloads dominate cloud environments.

From a SOC perspective, cloud security focuses on:
- Identity and access
- Metadata services
- API abuse
- Lateral movement via IAM
- Persistence using cloud-native features

Cloud attacks rarely stop at the host.

---

## 🧱 Shared Responsibility Model
Cloud providers secure:
- Physical infrastructure
- Core cloud services

You secure:
- Linux hosts
- IAM permissions
- Network access
- Logging and monitoring

Misunderstanding this leads to breaches.

---

## 🔑 Common Linux Cloud Attack Techniques

## 1️⃣ Metadata Service Abuse
Attackers query metadata services to steal credentials.

SOC indicators:
- Requests to metadata IPs (e.g. `169.254.169.254`)
- Metadata access from unexpected processes

---

## 2️⃣ IAM Credential Abuse
Stolen credentials are used to:
- Access APIs
- Create new resources
- Establish persistence

SOC indicators:
- API calls from non-management hosts
- New IAM users or keys after host compromise

---

## 3️⃣ Over-Permissive Security Groups
Open ports expose Linux services.

SOC indicators:
- SSH open to the world
- Unused services exposed externally

---

## 4️⃣ Cloud Persistence
Attackers persist via:
- New IAM users
- New access keys
- Startup scripts
- Cloud-init abuse

SOC indicators:
- Changes in cloud configs after intrusion
- Persistence without host-level artifacts

---

## 🧩 MITRE ATT&CK Mapping
- Initial Access
- Persistence
- Credential Access
- Lateral Movement
- Impact
