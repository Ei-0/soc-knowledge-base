# ⚔️ Windows Common Attacks

## 📌 Overview
Windows is the most targeted operating system in enterprise environments.

From a **SOC perspective**, understanding common Windows attacks helps analysts:
- Recognize attacker behavior quickly
- Correlate alerts into attack chains
- Map activity to MITRE ATT&CK
- Respond faster and more accurately

Most attacks reuse the same techniques with different tools.

---

## 🧱 Typical Windows Attack Lifecycle
A common Windows attack follows this pattern:
1. Initial Access
2. Execution
3. Persistence
4. Privilege Escalation
5. Credential Access
6. Lateral Movement
7. Defense Evasion
8. Impact

SOC analysts should focus on **behavior**, not malware names.

---

## 🔓 1. Initial Access Attacks

### 🔹 Phishing
Most common entry point:
- Malicious email attachments
- Embedded links
- HTML smuggling

🔍 **SOC Indicators**:
- Office applications spawning scripts
- User execution shortly after email delivery

---

### 🔹 Malicious Downloads
Users download:
- Fake installers
- Cracked software
- Trojanized tools

🔍 **SOC Indicators**:
- Execution from Downloads or Temp folders
- Unknown executables signed or unsigned

---

## ▶️ 2. Execution Techniques

### 🔹 Script-Based Execution
Attackers rely heavily on:
- PowerShell
- CMD
- WMI
- MSHTA

🔍 **SOC Indicators**:
- Encoded or obfuscated commands
- Scripts launched by user applications

---

### 🔹 Living Off the Land (LOLBins)
Abuse of legitimate binaries:
- rundll32
- regsvr32
- certutil

🔍 **SOC Indicators**:
- LOLBins used in unusual contexts
- Network activity from trusted binaries

---

## ♻️ 3. Persistence Techniques
Common persistence methods:
- Registry autorun keys
- Scheduled tasks
- Windows services
- Startup folders
- WMI subscriptions

🔍 **SOC Indicators**:
- Persistence created shortly after execution
- Persistence pointing to user-writable paths

---

## ⬆️ 4. Privilege Escalation

### 🔹 Exploiting Vulnerable Drivers
Attackers load vulnerable drivers to:
- Gain SYSTEM privileges
- Disable security controls

🔍 **SOC Indicators**:
- New driver installations
- Driver loads from unusual paths

---

### 🔹 UAC Bypass
Attackers bypass User Account Control:
- No prompt shown
- Silent elevation

🔍 **SOC Indicators**:
- Admin-level actions without user interaction

---

## 🔐 5. Credential Access

### 🔹 Credential Dumping
Targets include:
- LSASS memory
- Credential Manager
- Browser-stored credentials

🔍 **SOC Indicators**:
- Access to LSASS
- Memory dump activity
- Security tool tampering

---

### 🔹 Kerberos Attacks
Common techniques:
- Pass-the-Hash
- Pass-the-Ticket
- Kerberoasting

🔍 **SOC Indicators**:
- Abnormal Kerberos ticket usage
- Authentication from unexpected hosts

---

## 🌐 6. Lateral Movement
Attackers move between systems using:
- SMB
- RDP
- WMI
- Remote services

🔍 **SOC Indicators**:
- Authentication from non-standard systems
- Admin logins outside business hours

---

## 🛡️ 7. Defense Evasion
Attackers attempt to:
- Disable AV / EDR
- Clear event logs
- Obfuscate commands
- Masquerade processes

🔍 **SOC Indicators**:
- Log clearing events
- Security service stops
- Tampering with monitoring tools

---

## 💥 8. Impact

### 🔹 Ransomware
Final impact often includes:
- File encryption
- Shadow copy deletion
- System lockout

🔍 **SOC Indicators**:
- Mass file modifications
- Sudden service stoppages
- Backup tampering

---

## 🧠 SOC Detection Strategy
Effective SOC detection focuses on:
- Parent-child process anomalies
- Command-line analysis
- Persistence creation
- Credential access attempts
- Multi-event correlation

One alert ≠ one incident.

---

## 🧩 Mapping to MITRE ATT&CK
Windows common attacks span nearly all ATT&CK tactics:
- Initial Access
- Execution
- Persistence
- Privilege Escalation
- Credential Access
- Lateral Movement
- Defense Evasion
- Impact

Strong Windows visibility = strong SOC capability.

---

## 🧪 Example Attack Chain
1. Phishing email received
2. User opens document
3. PowerShell executes payload
4. Registry persistence added
5. Credentials dumped
6. Lateral movement via SMB
7. Ransomware deployed

SOC detection succeeds when this chain is **broken early**.

---

## 🚀 What’s Next?
Continue with:

👉 **`Windows-Forensics-Artifacts.md`**

This will focus on artifacts used during investigations and incident response.
