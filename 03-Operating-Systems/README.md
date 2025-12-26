# 🖥️ 03-Operating-Systems

## 📌 Overview
This section covers **Operating Systems from a security (SOC / DFIR) perspective**, focusing on:
- How operating systems work internally
- Where activities leave traces (logs & artifacts)
- How attackers abuse OS components
- How SOC analysts detect malicious behavior

Operating systems are the **primary battlefield of cyber attacks**.  
Every process, service, and login leaves artifacts that can be analyzed.

---

## 🎯 Learning Objectives
After completing this section, you will be able to:

- Understand operating system internals (Kernel vs User Mode)
- Analyze suspicious processes and services
- Read and interpret OS logs effectively
- Detect persistence mechanisms
- Correlate attacks with OS-level behavior
- Investigate incidents on:
  - Windows
  - Linux
  - macOS

---

## 🧱 Section Structure

### 🔹 OS Fundamentals
Core concepts shared across all operating systems:
- What is an Operating System?
- Kernel vs User Mode
- Processes & Threads
- Memory Management
- File Systems

### 🔹 Windows
Primary focus due to enterprise dominance:
- Windows Architecture
- Processes & Services
- Registry
- Event Logs
- Persistence Mechanisms
- Common Attacks
- Forensics Artifacts

### 🔹 Linux
Critical for servers and cloud environments:
- Linux Architecture
- Permissions & Ownership
- Logs
- Persistence
- Common Attacks & Artifacts

### 🔹 macOS
Increasingly important in modern enterprises:
- macOS Architecture
- Processes
- Logs
- Persistence
- Common Attacks

---

## 🔐 Authentication & Accounts
Understand how systems manage:
- Users and Groups
- Privileges and Permissions
- Credential Storage

---

## 📊 Logs & Monitoring
Because **logs are the eyes of the SOC**:
- OS logs overview
- What SOC analysts monitor
- Event correlation techniques

---

## 🧠 Persistence Techniques
How attackers maintain access:
- Startup mechanisms
- Scheduled tasks & cron jobs
- Services and daemons

---

## 🧪 SOC Scenarios (Hands-On Thinking)
Real-world inspired scenarios:
- Suspicious process detection
- Unauthorized administrator creation
- Persistence discovery

---

## 📎 Cheatsheets
Quick reference for SOC analysts:
- Important system paths
- Critical logs
- Investigation checklists

---

## 🧭 How SOC Analysts Use This Section
SOC analysts rely on this section when:
- Investigating EDR alerts
- Analyzing suspicious logins
- Detecting persistence mechanisms
- Supporting incident response
- Building attack timelines

---

## 🚀 What’s Next?
Start with the foundation:

👉 **OS-Fundamentals/What-Is-Operating-System.md**
