# macOS SSH & Remote Access — Access, Abuse & SOC Detection (DFIR)



---

## Overview

Remote access on macOS is **disabled by default** and tightly integrated with:
- System Settings  
- User permissions  
- Unified Logging  

When enabled or abused, it becomes a **high‑impact attack vector**.

SOC analysts should treat unexpected remote access as **high priority**.

---

## SSH on macOS

macOS includes OpenSSH by default.

Service name:
- `sshd`

Default state:
- Disabled  
- Enabled via:  
  **System Settings → General → Sharing → Remote Login**

🚩 **SSH enabled without business justification is suspicious.**

---

## SSH Configuration

Configuration file:

```
/etc/ssh/sshd_config
```

SOC considerations:
- Root login is disabled by default  
- Password authentication may be enabled  
- Configuration changes require admin privileges  

---

## Authentication Methods

Supported SSH authentication:
- Password‑based  
- Public key authentication  

Artifacts:

```
~/.ssh/authorized_keys
```

🚩 **New SSH keys added without user awareness are critical indicators.**

---

## SSH Execution Flow

```
launchd
└── sshd
    └── user shell
        └── commands
```

SOC Detection:
- `sshd` spawning shells  
- Network tools executed post‑login  

---

## SSH Logging (Unified Logs)

SSH events are logged in Unified Logs.

Relevant subsystems:
- `com.apple.sshd`  
- `com.apple.authd`  
- `com.apple.security`  

Example:

```bash
log show --predicate 'process == "sshd"' --last 24h
```

---

## SSH Abuse Scenarios

### Unauthorized SSH Enablement
- Attacker enables Remote Login  
- Gains persistent remote access  

### SSH Key Persistence
- Attacker adds a public key  
- Maintains access without passwords  

### Lateral Movement
- macOS used to pivot into Linux or cloud environments  

---

## Screen Sharing & Remote Management

macOS supports:
- **Screen Sharing** (VNC‑based)  
- **Remote Management (ARD)**  

Enabled via:
**System Settings → Sharing**

🚩 **Unexpected enablement is suspicious.**

Artifacts:
- Unified Logs  
- System settings changes  

---

## Apple Remote Desktop (ARD)

Used for enterprise management.

Capabilities:
- Screen control  
- File transfer  
- Command execution  

Attacker abuse:
- Silent remote control  
- Living‑off‑the‑land remote access  

---

## Detection Strategies

Monitor for:
- SSH enabled events  
- New `authorized_keys` entries  
- Remote access services enabled  
- Remote sessions outside business hours  
- SSH from unusual source IPs  

---

## Incident Response Notes

- Disable remote access immediately if unauthorized  
- Rotate user credentials  
- Review SSH keys  
- Correlate login events with logs  
- Check persistence mechanisms  

---

## Key Takeaways

- SSH is powerful and dangerous on macOS  
- Disabled‑by‑default services matter  
- Key‑based persistence is stealthy  
- Unified Logs are critical for detection  
- Remote access equals high risk  

---
