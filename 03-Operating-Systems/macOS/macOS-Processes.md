# macOS Processes — Execution, Hierarchy & Detection (SOC / DFIR)


---

## Overview

Process analysis is one of the **most important skills** for detecting attacks on macOS.

Unlike Windows, macOS relies heavily on:
- Trusted parent processes
- GUI-driven execution
- User-space persistence

Attackers abuse this trust model to blend in.

---

## macOS Process Model

macOS uses a **parent–child process hierarchy** where **every process ultimately traces back to `launchd` (PID 1)**.

Key characteristics:
- Strong reliance on trusted parents
- GUI applications are common parents
- Command-line activity is less common on end-user Macs

---

## launchd — Root of All Processes

`launchd` is the first user-space process.

Responsibilities:
- Spawning system and user services
- Managing background jobs
- Loading persistence mechanisms
- Acting as PID 1

Example:
```
launchd (1)
├── system services
├── user services
└── loginwindow
```

🚩 Any malicious activity tied to `launchd` often indicates **persistence**.

---

## Process Creation Flow

macOS follows the traditional UNIX model:

```
fork() → child process created
exec() → new program loaded
```

- `fork()` duplicates the process  
- `exec()` replaces memory with a new binary  
- PID remains the same after exec  

### SOC Insight
Most attacks occur during **exec**, not fork.

---

## Parent–Child Relationship (Critical for Detection)

Example benign flow:
```
launchd
└── loginwindow
    └── Finder
        └── Safari
```

Example suspicious flow:
```
launchd
└── Finder
    └── bash
        └── curl
```

🚩 Red Flags:
- GUI apps spawning shells  
- System services spawning network tools  
- Browsers launching interpreters  

---

## Common Trusted Parents Abused by Attackers

Attackers prefer parents that appear legitimate:

- launchd  
- Finder  
- loginwindow  
- SystemUIServer  
- Dock  
- Safari / Chrome  

These parents reduce user suspicion and bypass naive detections.

---

## Living-off-the-Land Binaries (LOLBins)

Common macOS LOLBins abused in attacks:

- osascript  
- bash / zsh  
- sh  
- curl  
- python  
- ruby  
- perl  
- launchctl  
- plutil  

🚩 Context matters more than the binary itself.

---

## GUI vs CLI Execution

### GUI-driven execution
- More common on macOS  
- Harder for SOC tools to flag  
- Often triggered by user interaction  

### CLI-driven execution
- Less common on end-user Macs  
- High-signal in non-developer environments  

🚩 Terminal usage on executive laptops is often suspicious.

---

## Process States (macOS / BSD)

| State | Meaning |
|-------|---------|
| R | Running |
| S | Sleeping |
| D | Uninterruptible sleep |
| T | Stopped |
| Z | Zombie |

### Detection Note
Persistent zombies may indicate:
- Broken malware  
- Failed persistence  
- Process injection attempts  

---

## Code Signing & Processes

Every executable process on macOS has:
- A signing status  
- A developer identity (or none)  

SOC considerations:
- Signed ≠ Safe  
- Unsigned ≠ Malicious  
- Parent + behavior define risk  

🚩 Signed malware abusing Apple trust is common.

---

## Process Injection (macOS Reality)

macOS restricts:
- ptrace  
- task_for_pid  
- dylib injection  

Attackers adapt by using:
- Script-based execution  
- User-approved automation  
- Abusing Accessibility permissions  

---

## Detection Strategies for SOC

Focus on:
- Parent-child anomalies  
- GUI apps spawning interpreters  
- launchd spawning unsigned binaries  
- Network tools spawned by non-network apps  
- Execution from user-writable directories  

---

## Key Takeaways

- Parent process context is critical on macOS  
- launchd abuse = high confidence malicious activity  
- GUI-driven execution is attacker-friendly  
- Behavior > binary  
- macOS process analysis requires context, not signatures  

---
