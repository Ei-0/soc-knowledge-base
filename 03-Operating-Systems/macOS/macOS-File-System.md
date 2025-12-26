# macOS File System — Layout, Permissions & Forensics (SOC / DFIR)



---

## Overview

The macOS file system is designed for **security, integrity, and recovery**, not investigator convenience.

Key differences from Linux:
- Read-only system volume  
- APFS snapshots  
- Heavy use of user-space directories  
- Extended attributes and metadata  

Understanding the layout is critical for **malware hunting, persistence detection, and forensics**.

---

## APFS — Apple File System

macOS uses **APFS** with features relevant to DFIR:

- Volume groups (System + Data)  
- Snapshots  
- Copy-on-write  
- Strong metadata tracking  
- Encryption by default  

### Volume Structure

```
APFS Container
├── Macintosh HD (System Volume - Read-only)
├── Macintosh HD - Data (User & App Data)
└── Preboot / Recovery
```

**SOC Note:**
- System Volume is cryptographically sealed  
- Malware typically lives in the Data volume  

---

## System Volume vs Data Volume

### System Volume (Read-Only)
- /System  
- /bin  
- /sbin  
- /usr (mostly)  

Protected by:
- SIP  
- Sealed System Volume (SSV)  

### Data Volume (Writable)
- /Applications  
- /Library  
- /Users  
- /opt  
- /usr/local  

🚩 **Malicious writes to System Volume = advanced compromise.**

---

## Key Directories for SOC & DFIR

### /Applications
- Legitimate app bundles  
- Fake or trojanized apps often placed here  

🚩 Look for:
- Recently added apps  
- Apps with generic names  

---

### /Library
System-wide resources and persistence.

Important subdirectories:
- /Library/LaunchDaemons  
- /Library/LaunchAgents  
- /Library/Extensions (restricted)  
- /Library/Preferences  

---

### /Users

Each user has a home directory:

```
/Users/username/
├── Desktop
├── Documents
├── Downloads
└── Library
```

Most user-space malware lives here.

---

## User Library (High-Value Target)

Path:

```
~/Library/
```

Critical subfolders:
- LaunchAgents  
- Application Support  
- Preferences  
- Caches  
- Logs  

🚩 Attackers prefer **user-level persistence** to bypass SIP.

---

## Permissions Model

macOS permissions combine:
- POSIX permissions  
- ACLs  
- Extended Attributes (xattrs)  

Example:

```bash
ls -le
```
## Extended Attributes (xattrs)

Extended attributes include:

- `com.apple.quarantine`
- `com.apple.metadata`

🚩 **Removing quarantine is a common malware technique.**

---

## Quarantine Attribute

Files downloaded from the internet receive:

```
com.apple.quarantine
```

### Purpose:
- Gatekeeper enforcement

### Attacker techniques:
- Removing quarantine flag  
- Transferring files via trusted apps  

---

## Symbolic Links & Firmlinks

macOS uses **firmlinks** to connect:

- System Volume  
- Data Volume  

This can confuse:
- Investigators  
- Scripts  
- Security tools  

**SOC Tip:**  
Always resolve **real paths** during analysis.

---

## Hidden Files & Metadata Abuse

Attackers may hide payloads using:
- Dotfiles  
- Deep nested folders  
- Legitimate app support paths  
- Extended attributes  

---

## Forensics Considerations

- Full Disk Access is required  
- SIP limits live analysis  
- APFS snapshots can aid timeline analysis  
- Time Machine backups are valuable artifacts  

---

## Detection Tips

Focus on:
- Executables in user-writable directories  
- Persistence files in Library paths  
- Modified LaunchAgents  
- Unexpected binaries in Application Support  
- Recently changed extended attributes  

---

## Key Takeaways

- macOS file system is **security-first**  
- User Library is the primary malware playground  
- System Volume modification is rare and high‑risk  
- Extended attributes matter  
- Context beats path‑only detections  
