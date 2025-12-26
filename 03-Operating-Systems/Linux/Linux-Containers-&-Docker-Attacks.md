# 🐳 Linux Containers & Docker Attacks (SOC & DFIR)

## 📌 Overview
Containers and Docker are widely used in Linux environments, especially in cloud and DevOps pipelines.

From a SOC and DFIR perspective, container security matters because:
- Containers often run with excessive privileges
- Misconfigurations enable host escape
- Compromised containers are used as pivot points
- Monitoring is often weaker than on hosts

Container ≠ sandbox by default.

---

## 🧱 How Docker Works (Security Context)
Docker relies on:
- Linux namespaces
- cgroups
- Overlay filesystems
- Docker daemon (often running as root)

SOC relevance:
- Compromise of Docker daemon = compromise of host
- Containers inherit kernel from host

---

## 🔓 Common Docker & Container Attack Techniques

## 1️⃣ Exposed Docker Daemon
If Docker API is exposed:
- Attackers can create containers
- Mount host filesystem
- Execute commands as root

SOC indicators:
- Docker API listening on TCP
- Container creation from unknown sources

---

## 2️⃣ Privileged Containers
Privileged containers bypass isolation.

SOC indicators:
- Containers running with `--privileged`
- Access to `/dev` or host kernel interfaces

---

## 3️⃣ Host File System Mount Abuse
Attackers mount host paths inside containers.

SOC indicators:
- Containers with `/`, `/etc`, or `/var/run/docker.sock` mounted
- Modification of host files from container context

---

## 4️⃣ Docker Socket Abuse
Mounting `/var/run/docker.sock` allows full Docker control.

SOC indicators:
- Containers accessing Docker socket
- Docker commands executed from containers

---

## 5️⃣ Container Escape
Attackers exploit kernel or misconfigurations to escape container.

SOC indicators:
- Container process spawning host-level processes
- Unexpected kernel-level activity

---

## 🚨 High-Risk Container Indicators
- Containers running as root
- Network scanning from containers
- Containers initiating outbound C2 traffic
- New containers created after compromise

---

## 🧩 MITRE ATT&CK Mapping
- Privilege Escalation
- Defense Evasion
- Lateral Movement
- Impact
