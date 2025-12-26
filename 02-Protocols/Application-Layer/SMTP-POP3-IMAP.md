# SMTP, POP3 & IMAP (SOC Analyst Perspective)

Email protocols are a primary attack vector in most environments.  
SMTP is used to send emails, while POP3 and IMAP are used to retrieve them.  
Attackers heavily abuse email protocols for phishing, malware delivery, and data exfiltration.

---

## What These Protocols Do
- SMTP: Sends email between clients and mail servers
- POP3: Downloads email from a server to a client
- IMAP: Synchronizes email between server and client
<img width="1200" height="628" alt="image" src="https://github.com/user-attachments/assets/cea15a79-8421-4cad-b997-ff604fab2cac" />

Used for:
- Corporate email communication
- Notifications and alerts
- Automated system emails

---

## Normal Behavior
Typical email protocol behavior includes:
- SMTP traffic from known mail servers
- POP3/IMAP access from user endpoints
- Predictable login patterns
- Consistent server destinations
- Regular business-hour activity

---

## SOC Visibility
SOC analysts observe email protocols through:
- Email gateway logs
- Mail server logs
- Firewall logs
- IDS/IPS alerts
- EDR network telemetry

Common fields:
- Sender and recipient addresses
- Source and destination IPs
- Authentication results
- Attachment metadata
- Message size
- Connection timestamps

---

## Common Abuse Patterns

### Phishing Delivery
Attackers send malicious emails to steal credentials or deliver malware.
<img width="2676" height="4679" alt="image" src="https://github.com/user-attachments/assets/66b34248-f462-4905-ace8-86589c0fba3d" />

Indicators:
- Emails from newly registered or spoofed domains
- Suspicious attachments or links
- High volume of similar emails
- Failed SPF, DKIM, or DMARC checks
<img width="2163" height="1128" alt="image" src="https://github.com/user-attachments/assets/0f187550-087d-4143-acb3-af4afdacceca" />

---

### Malware Delivery
Malware is delivered via attachments or malicious links.

Indicators:
- Executable or macro-enabled attachments
- Abnormal attachment sizes
- External senders targeting many users

---

### Credential Abuse
Compromised accounts are used to send or access email.

Indicators:
- Logins from unusual locations
- Multiple failed authentication attempts
- Sudden spikes in outbound email volume
- POP3/IMAP access from unexpected IPs

---

## Indicators of Suspicious Email Protocol Activity
- SMTP traffic originating from user endpoints
- Excessive outbound emails (possible spam or compromise)
- POP3/IMAP logins outside normal hours
- Access from foreign or rare IP ranges
- Email activity without user presence

---

## SOC Investigation Tips
1. Identify affected users and mailboxes
2. Analyze sender reputation and domain age
3. Review authentication logs and failures
4. Inspect attachment hashes and URLs
5. Correlate with endpoint activity
6. Check for lateral phishing attempts

---

## Practice Mapping
Commonly used during:
- Phishing investigations
- Business email compromise (BEC)
- Malware delivery analysis
- Incident response
- Detection tuning

---

## Key Takeaway
Email remains the **most effective initial access vector**.  
Strong SOC visibility and rapid response are critical.
