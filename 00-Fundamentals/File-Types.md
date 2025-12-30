# 📁 File Types & Extensions — SOC Analyst Reference

## 🎯 Purpose

Understanding file types is critical for SOC analysts to:
- Identify malicious payloads
- Assess attachment risk
- Detect execution techniques
- Analyze malware delivery methods
- Apply correct security controls

File extensions often indicate **capability**, **intent**, and **risk level**.

---

## 1️⃣ Executable Files (High Risk)

These files can **execute code directly**.

| Extension | Full Name | Usage | SOC Notes |
|--------|----------|------|----------|
| .exe | Executable | Windows application | Most common malware format |
| .dll | Dynamic Link Library | Shared code library | Used in DLL hijacking |
| .sys | System File | Kernel drivers | Rootkits / drivers |
| .com | Command File | Legacy executable | Often abused |
| .msi | Windows Installer | Software installer | Malware delivery |
| .scr | Screen Saver | Executable | Common phishing payload |
| .app | Application | macOS app bundle | Malware on macOS |
| .bin | Binary File | Raw binary | Needs context |
| .elf | Executable & Linkable Format | Linux binaries | Linux malware |

---

## 2️⃣ Script Files (Execution via Interpreter)

Executed by scripting engines.

| Extension | Language | Usage | SOC Notes |
|--------|--------|------|----------|
| .ps1 | PowerShell | Automation | Living-off-the-land |
| .bat | Batch | Windows scripts | Initial access |
| .cmd | Command | Windows scripts | Similar to .bat |
| .vbs | VBScript | Automation | Legacy malware |
| .js | JavaScript | Web / scripting | Email attachments |
| .jse | Encoded JS | Obfuscated JS | Malware delivery |
| .py | Python | Scripting | Post-exploitation |
| .sh | Shell Script | Linux/macOS | Persistence |
| .pl | Perl | Scripting | Older attacks |

---

## 3️⃣ Office Documents (User-Triggered Risk)

Require user interaction.

| Extension | Application | Usage | SOC Notes |
|--------|------------|------|----------|
| .doc | Word | Document | Macro abuse |
| .docx | Word | Document | Can embed exploits |
| .docm | Word Macro | Document | High-risk |
| .xls | Excel | Spreadsheet | Macro abuse |
| .xlsx | Excel | Spreadsheet | Formula abuse |
| .xlsm | Excel Macro | Spreadsheet | High-risk |
| .ppt | PowerPoint | Presentation | Embedded payloads |
| .pptm | PowerPoint Macro | Presentation | High-risk |
| .rtf | Rich Text | Document | Exploit vectors |

---

## 4️⃣ Archive / Compressed Files

Used to **hide payloads** and bypass filters.

| Extension | Format | Usage | SOC Notes |
|--------|-------|------|----------|
| .zip | ZIP Archive | Compression | Common delivery |
| .rar | RAR Archive | Compression | Password-protected |
| .7z | 7-Zip | Compression | Strong encryption |
| .tar | Tape Archive | Linux archive | Often combined |
| .gz | Gzip | Compression | Linux environments |
| .iso | Disk Image | Virtual media | Malware delivery |
| .cab | Cabinet | Windows archive | Malware packaging |

---

## 5️⃣ Web & Internet Files

Used in phishing and web attacks.

| Extension | Type | Usage | SOC Notes |
|--------|------|------|----------|
| .html | HTML | Web page | Credential harvesting |
| .htm | HTML | Web page | Phishing pages |
| .php | PHP Script | Server-side | Web shells |
| .asp | Active Server Page | Server-side | Legacy webshells |
| .jsp | Java Server Page | Server-side | Java web attacks |
| .css | Style Sheet | Web design | Rarely malicious |
| .json | Data Format | APIs | Config exfiltration |

---

## 6️⃣ Shortcut & Link Files

Used for **execution redirection**.

| Extension | Type | Usage | SOC Notes |
|--------|------|------|----------|
| .lnk | Shortcut | Windows link | LOLBins abuse |
| .url | Internet Shortcut | Web link | Phishing redirection |
| .desktop | Linux Shortcut | App launcher | Persistence |

---

## 7️⃣ Email-Related Files

Seen during phishing analysis.

| Extension | Type | Usage | SOC Notes |
|--------|------|------|----------|
| .eml | Email Message | Email storage | Evidence |
| .msg | Outlook Message | Email storage | Header analysis |
| .pst | Outlook Data | Mailbox | Data exfiltration |
| .ost | Outlook Cache | Mailbox | Forensics |

---

## 8️⃣ Media Files (Can Be Weaponized)

Normally safe, sometimes abused.

| Extension | Type | Usage | SOC Notes |
|--------|------|------|----------|
| .pdf | PDF Document | Documents | Exploits / JS |
| .jpg | Image | Media | Steganography |
| .png | Image | Media | Payload hiding |
| .mp3 | Audio | Media | Rare abuse |
| .mp4 | Video | Media | Rare abuse |

---

## 9️⃣ Configuration & System Files

Reveal environment details.

| Extension | Type | Usage | SOC Notes |
|--------|------|------|----------|
| .ini | Config | App settings | Credential leaks |
| .conf | Config | Linux configs | Security settings |
| .xml | Markup | Config / data | XXE attacks |
| .yaml | Config | Cloud / DevOps | Secrets exposure |
| .env | Environment | App secrets | High-value target |
| .reg | Registry | Windows registry | Persistence |

---

## 🔟 Disk & Memory Files

Used in DFIR.

| Extension | Type | Usage | SOC Notes |
|--------|------|------|----------|
| .dmp | Dump | Memory dump | Credential extraction |
| .img | Disk Image | Forensics | Evidence |
| .vhd | Virtual Disk | VM storage | Malware lab |
| .vmdk | VM Disk | Virtual machines | Investigation |

---

## 🧠 SOC Analyst Key Takeaways

- File extensions indicate **capability**, not intent
- Double extensions (invoice.pdf.exe) are red flags
- Macro-enabled files are high risk
- Archives + passwords = common malware tactic
- Scripts enable stealthy execution
- Always verify MIME type vs extension

---

## 🏁 Summary

File type awareness enables SOC analysts to:
- Detect malicious delivery
- Prioritize alerts
- Improve phishing analysis
- Understand attacker execution paths

File extensions are **one of the first clues** in any investigation.

---
