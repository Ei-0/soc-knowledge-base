# 🔐 Cryptography Fundamentals (Encryption + Hashing) — SOC Reference

## 🎯 Learning Objective

A SOC analyst must understand cryptography to:
- Recognize secure vs insecure configurations (TLS, VPNs, SSH, email security)
- Investigate incidents involving encrypted traffic, ransomware, credential theft, and integrity tampering
- Interpret logs and indicators related to certificates, ciphers, hashes, and keys
- Communicate findings clearly to IR/DFIR and engineering teams

---

## 1) Core Concepts & Terminology

### ✅ Plaintext vs Ciphertext
- **Plaintext**: readable data (e.g., password, document, message)
- **Ciphertext**: encrypted (scrambled) data produced by an encryption algorithm

### ✅ Encryption vs Encoding vs Obfuscation
- **Encryption**: protects confidentiality using a key (reversible with the correct key)
- **Encoding**: changes representation for compatibility (Base64, URL encoding) — not security
- **Obfuscation**: makes data harder to read (often used by malware) — not true protection

### ✅ CIA Mapping
- **Confidentiality** → Encryption
- **Integrity** → Hashing / MAC / Digital Signatures
- **Authentication / Non-repudiation** → Digital Signatures, Certificates

---

## 2) Encryption: What It Is

**Encryption** is a process that transforms plaintext into ciphertext using:
- an **algorithm** (cipher)
- a **key**
- sometimes an **IV/nonce** (random value)

**Goal:** prevent unauthorized parties from reading data.

---

## 3) Types of Encryption

### A) Symmetric Encryption (Secret-Key)
**Same key** encrypts and decrypts.

**Pros**
- Very fast
- Best for bulk data (files, disks, network sessions)

**Cons**
- Key distribution problem (how to share the secret safely)

**Common Algorithms**
- **AES** (industry standard)
- **ChaCha20** (common in modern protocols)
- Legacy/weak: **DES**, **3DES**, **RC4** (avoid)

**Where SOC sees it**
- TLS session encryption (after handshake)
- Disk encryption (BitLocker, FileVault, LUKS)
- Ransomware file encryption (attackers use symmetric for speed)

---

### B) Asymmetric Encryption (Public-Key)
Two keys:
- **Public key** (shareable)
- **Private key** (secret)

Used for:
- Secure key exchange
- Digital signatures
- Identity/authentication

**Pros**
- Solves key sharing problem
- Enables signatures

**Cons**
- Slower than symmetric encryption

**Common Algorithms**
- **RSA**
- **ECC** (Elliptic Curve Cryptography): ECDSA, ECDH (modern + efficient)
- Avoid old/bad configs: RSA with short keys, weak curves, outdated padding

**Where SOC sees it**
- TLS handshake (certificate-based authentication)
- SSH authentication keys
- Email encryption/signing (S/MIME, PGP)

---

### C) Hybrid Encryption (Most Real Systems)
**Asymmetric** is used to securely exchange a session key,
then **symmetric** encrypts the data stream.

Example:
- HTTPS (TLS) = hybrid design

---

## 4) Encryption Modes (Critical!)

Encryption algorithms (like AES) use **modes** to encrypt multiple blocks.

### Common AES Modes
- **AES-GCM** ✅ (recommended): provides confidentiality + integrity (AEAD)
- **AES-CBC** ⚠️: confidentiality only; requires separate integrity protection (HMAC)
- **AES-CTR** ✅: stream-like; must combine with integrity (HMAC/AEAD)
- **AES-ECB** ❌ (bad): leaks patterns; never use

**SOC Tip**
If you see ECB in configs or code, treat as a security red flag.

---

## 5) IV / Nonce (Why It Matters)
- Prevents encrypting the same plaintext into the same ciphertext
- Must be **unique** (and sometimes unpredictable) depending on mode
- Reuse of nonce in stream modes (CTR/ChaCha20) can be catastrophic

---

## 6) Data at Rest vs Data in Transit

### Data at Rest
- Disk encryption (BitLocker/FileVault/LUKS)
- Database encryption (TDE)
- File encryption (EFS, app-level encryption)

**SOC signals**
- Unexpected encryption activity could be ransomware
- Key vault usage anomalies (KMS, HSM)

### Data in Transit
- TLS/HTTPS, VPN, SSH, IPsec
- Messaging security (Signal protocol, etc.)

**SOC signals**
- TLS certificate anomalies
- Weak cipher negotiation
- Suspicious encrypted tunnels / beaconing

---

## 7) Hashing: What It Is (Not Encryption)

A **hash function** maps data of any size to fixed-size output.

Key properties:
- **One-way** (cannot be reversed)
- **Deterministic** (same input → same hash)
- **Avalanche effect** (small change → huge output change)

**Hashing is used for**
- Integrity verification
- File identification (malware analysis)
- Password storage (with proper hashing schemes)

---

## 8) Hash Types (Algorithms)

### Modern Secure Hash Functions
- **SHA-256 / SHA-512** ✅
- **SHA-3** ✅ (less common but solid)
- **BLAKE2 / BLAKE3** ✅ (fast, modern)

### Weak / Deprecated
- **MD5** ❌ (collisions)
- **SHA-1** ❌ (collisions)

**SOC Tip**
MD5/SHA1 are still used for *identification* in malware repos,
but do not treat them as secure integrity mechanisms.

---

## 9) Hashing vs Password Hashing (Very Important)

### General Hashing (Integrity)
- SHA-256 on a file to verify it wasn’t modified

### Password Hashing (Storage)
Passwords must be stored using **slow, salted** hashing algorithms:
- **bcrypt** ✅
- **scrypt** ✅
- **Argon2** ✅ (best modern choice)

**Never store passwords using**
- MD5 / SHA1 / plain SHA256 alone ❌

---

## 10) Salt, Pepper, and Why They Matter

### Salt
Random value stored with the password hash.
- Prevents rainbow table attacks
- Ensures identical passwords have different hashes

### Pepper
A secret value stored separately (e.g., in an HSM or secure config).
- Adds extra protection if DB leaks

---

## 11) Integrity Mechanisms Beyond Hashing

### A) MAC (Message Authentication Code)
Ensures integrity + authenticity using a shared secret key.

Common:
- **HMAC-SHA256** ✅

Use case:
- API request signing
- Log integrity protections
- TLS legacy constructs (older approaches)

### B) Digital Signatures
Uses asymmetric crypto:
- Private key signs
- Public key verifies

Provides:
- Integrity
- Authentication
- Non-repudiation

Common:
- **RSA-PSS**, **ECDSA**
- Code signing certificates
- Software update validation

---

## 12) Certificates & PKI (SOC Must-Know)

### What a Certificate Does
A TLS certificate binds:
- a **public key**
- to an **identity** (domain/org)
Signed by a **Certificate Authority (CA)**.

### Key PKI Terms
- **CA**: entity that issues certs
- **Chain of trust**: root → intermediate → leaf cert
- **SAN**: Subject Alternative Name (domains covered)
- **Expiration**: cert validity period
- **Revocation**: CRL / OCSP

**SOC signals**
- Self-signed certs on critical services
- Expired certs causing fallback behavior
- Suspicious new cert issuance for internal domains
- TLS interception proxies (legitimate or malicious)

---

## 13) TLS Basics (SOC View)

### TLS Handshake (Simplified)
- ClientHello (offers cipher suites)
- ServerHello (selects suite + sends cert)
- Key exchange (ECDHE recommended)
- Session keys derived
- Encrypted communication begins

### What SOC Should Look For
- Deprecated TLS versions (TLS 1.0/1.1) ❌
- Weak ciphers (RC4, 3DES) ❌
- Lack of forward secrecy (no ECDHE) ⚠️
- Odd SNI values (domain mismatch)
- Cert anomalies (issuer, SAN, CN mismatch)

---

## 14) Common Attacker Abuses of Crypto

### A) Ransomware
- Encrypts files with symmetric keys (AES)
- Protects the AES key with attacker public key (RSA/ECC)
- Leaves ransom note + deletes shadow copies (often)

### B) Encrypted C2 (Command & Control)
- Uses HTTPS/TLS to hide traffic
- Domain fronting (sometimes)
- Self-signed certs or short-lived certs

### C) Password Attacks
- Offline cracking of leaked hashes
- Pass-the-hash (Windows NTLM)
- Credential stuffing using breached passwords

### D) Hash Collisions (Older Hashes)
- MD5/SHA1 collisions can be used to bypass integrity checks in weak systems

---

## 15) SOC Practical Cheatsheet

### When You See Encryption in Logs, Ask:
- What protocol? (TLS/SSH/VPN)
- What version? (TLS 1.2 vs 1.3)
- What cipher suite?
- What certificate issuer?
- Is the domain expected?
- Is it a known corporate proxy?
- Is it beaconing behavior?

### When You See Hashes, Ask:
- What algorithm? (SHA256 vs MD5)
- Is it for integrity, identification, or password storage?
- Is salting used (password hashes)?
- Is this hash associated with known malware (VT, MISP, TI feeds)?

---

## 16) Mini Lab (Exercises)

### Exercise 1: File Integrity
1. Take a file and compute SHA256
2. Modify a single byte
3. Recompute SHA256
4. Observe avalanche effect

### Exercise 2: Identify Weak Hash Usage
Given a system storing passwords as SHA1:
- Explain why it’s weak
- Recommend bcrypt/Argon2 + salt + rate limiting

### Exercise 3: TLS Hygiene
Given a service supporting TLS 1.0 and 3DES:
- Identify risks
- Recommend TLS 1.2/1.3 + strong AEAD suites

---

## 🏁 Summary

- **Encryption** protects confidentiality (symmetric/asymmetric/hybrid)
- **Hashing** is one-way and supports integrity and identification
- **Password hashing** requires slow salted algorithms (Argon2/bcrypt)
- **MACs and signatures** provide integrity + authenticity
- **Certificates and TLS** are core SOC investigation surfaces
- Attackers abuse encryption for ransomware and encrypted C2

---
