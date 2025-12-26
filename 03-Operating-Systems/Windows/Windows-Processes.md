# ⚙️ Windows Processes

<img width="1600" height="1037" alt="image" src="https://github.com/user-attachments/assets/c0a5336c-3d7a-4c97-b424-1e1024e9e19f" />

## 📌 Overview
A **Windows process** is an instance of a running program with its own:
- Virtual memory space
- Executable code
- Handles (files, registry, network)
- Security context (user privileges)

From a **SOC perspective**, process analysis is one of the **most powerful detection techniques**.

---

## 🧱 Core Components of a Windows Process
Each process includes:
- Executable image (.exe)
- One or more threads
- Virtual address space
- Access token (user & privileges)
- Handles to system resources

Understanding these components helps identify abuse and anomalies.

---

## 🔄 Process Creation in Windows
Process creation typically follows this flow:
1. A parent process calls a Windows API
2. The OS loads the executable into memory
3. Threads are initialized
4. Security token is assigned
5. The process begins execution

🔍 **SOC View**:
- Parent-child relationships are critical
- Abnormal creation chains often indicate attacks

---

## 👨‍👩‍👦 Parent–Child Process Relationships
Windows processes often spawn other processes.

### 🔹 Why This Matters
Many detections rely on **unexpected parent-child pairs**.

⚠️ Common Suspicious Examples:
- `winword.exe` → `powershell.exe`
- `excel.exe` → `cmd.exe`
- `outlook.exe` → `mshta.exe`
- Browser → `certutil.exe`

These chains are frequently used in phishing attacks.

---

## 🧵 Threads in Windows Processes
- Threads execute the actual code
- A single process can have many threads
- Threads share process memory

🔍 **SOC View**:
- Malicious code is often injected as a new thread
- Thread injection hides execution inside trusted processes

---

## 🚨 Common Process Abuse Techniques

### 🔹 Process Injection
Attackers inject code into legitimate processes to:
- Evade detection
- Bypass application controls

Common techniques:
- DLL Injection
- Process Hollowing
- Thread Hijacking

---

### 🔹 Living Off the Land (LOLBins)
Attackers abuse trusted Windows binaries:
- `powershell.exe`
- `cmd.exe`
- `wmi.exe`
- `mshta.exe`
- `rundll32.exe`

🔍 **SOC View**:
- Legitimate binaries performing malicious actions
- Context matters more than the binary itself

---

### 🔹 Masquerading
Malware disguises itself as legitimate processes:
- Similar names (e.g., `svch0st.exe`)
- Correct icons
- Runs from user directories

---

## 📊 What SOC Analysts Should Monitor
Key telemetry points:
- Process name & full path
- Parent process
- Command-line arguments
- User account
- Hash (SHA256)
- Network connections
- Loaded DLLs

EDR tools heavily rely on this data.

---

## 🧠 Behavioral Detection Tips
SOC analysts should look for:
- Processes running from unusual directories
- Office apps spawning scripting engines
- High-privilege processes started by low-privilege parents
- Legitimate tools used at unusual times

Behavior > Signatures.

---

## 🧩 Mapping to MITRE ATT&CK
Windows process abuse maps to:
- Execution
- Defense Evasion
- Privilege Escalation
- Persistence

Process analysis enables fast ATT&CK classification.

---

## 🧪 Real-World Example
1. User opens a phishing email attachment
2. `winword.exe` spawns `powershell.exe`
3. PowerShell downloads payload
4. Payload injects into `explorer.exe`
5. Malicious activity runs under a trusted process

This pattern is extremely common in enterprise attacks.

---

## 🚀 What’s Next?
Continue with:

👉 **`Windows-Services.md`**

This will cover how attackers abuse Windows services for persistence and privilege escalation.
