# Security Incident Report

**Incident Type:** Suspicious Account Login  
**Analyst:** Josphat Muchiri (Candor Labs)  
**Date:** 04/02/2026

---

## 1. Incident Summary
A login notification was received indicating access to an account from a new device and location.

- **Device:** Infinix X6819  
- **Location:** Nairobi, Kenya  
- **IP Address:** 105.164.31.17  

<img src="[/Portfolio/images/bolt-login-alert.png](https://jomuchiri.github.io/Portfolio/images/bolt-login-alert.png" alt="Suspicious Login Alert" width="600">

The login was flagged as unusual and required investigation.

---

## 2. Initial Assessment
The login attempt showed:
- A new device not previously associated with the account  
- A local IP address within the same geographic region  

This suggested either:
- Possible unauthorized access  
- Or legitimate access from a different device  

---

## 3. Investigation Steps
Actions taken:
- Reviewed account activity logs  
- Verified known devices associated with the account  
- Analyzed IP address and location data  
- Assessed potential credential exposure sources  

---

## 4. Findings
- No confirmed malicious transactions were observed  
- The login originated from a local network  
- Device type did not match the primary user device  

> **Conclusion:** Classified as a suspicious login attempt with potential credential exposure.

---

## 5. Risk Assessment

| Factor            | Risk   |
|-------------------|--------|
| Unknown device    | Medium |
| Same location     | Low    |
| No malicious activity | Low |

**Overall Risk Level:** Medium

---

## 6. Response Actions
- Password was changed immediately  
- All active sessions were terminated  
- Multi‑factor authentication recommended  
- Account activity monitored for anomalies  

---

## 7. Recommendations
- Use unique passwords across services  
- Enable two‑factor authentication (2FA)  
- Avoid logging into accounts on shared devices  
- Monitor account activity regularly  

---

## 8. Conclusion
This incident highlights the importance of:
- Monitoring login alerts  
- Responding quickly to suspicious activity  
- Implementing strong authentication controls  
