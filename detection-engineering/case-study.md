# Detection Engineering Case Studies

**Part of Candor Labs** | Ongoing Project

This section documents custom detection rules I developed and tested in my home SOC lab using **Sysmon + Wazuh**. The goal was to move from generic alerts to high-fidelity detections that reduce noise and catch real threats.

## Project Overview

I focused on creating detections for common attack techniques seen in real-world environments, particularly:
- Web application attacks
- Brute force attempts
- Malicious document macros
- MSHTML exploits

## Key Detections Developed

### 1. Web Attack Detection
- **Technique**: SQL Injection & XSS attempts
- **Data Source**: Wazuh + Web server logs
- **Rule Logic**: Pattern matching for common SQLi payloads and encoded XSS strings
- **Outcome**: Successfully reduced false positives while maintaining good coverage

### 2. Brute Force Attack Detection
- **Technique**: Multiple failed login attempts (MITRE T1110)
- **Data Source**: Windows Event Logs + Sysmon
- **Rule Logic**: Threshold-based detection (e.g., >10 failed logins in 5 minutes from same IP)
- **Outcome**: Early identification of credential stuffing attempts

### 3. Malicious Document Triage (VBA & Excel 4.0 Macros)
- **Technique**: Malicious macro execution (MITRE T1566.001)
- **Data Source**: Sysmon Event ID 1 & 11
- **Rule Logic**: Monitoring for suspicious process creation from Office applications (winword.exe, excel.exe spawning cmd.exe or powershell.exe)
- **Outcome**: Effective at catching weaponized documents

### 4. MSHTML Exploit Detection
- **Technique**: Exploitation of MSHTML control (MITRE T1218.005)
- **Data Source**: Sysmon
- **Rule Logic**: Detection of unusual parent-child process relationships involving mshta.exe

## Challenges & Solutions

| Challenge                          | Solution |
|------------------------------------|--------|
| High volume of noisy alerts        | Tuned rules with appropriate thresholds and exclusions |
| Difficulty mapping to MITRE ATT&CK | Created clear rule documentation with ATT&CK technique mapping |
| Testing detections safely          | Used the isolated lab environment with controlled attack simulations |

## Tools & Technologies Used

- Sysmon (custom config)
- Wazuh (custom decoders & active response rules)
- MITRE ATT&CK Framework
- CyberChef for payload analysis

## Lessons Learned

- Detection engineering is an iterative process — start broad, then tune for precision.
- Combining Sysmon telemetry with Wazuh gives excellent visibility into endpoint behavior.
- Well-documented detections with clear reasoning help during handoff or escalation.

This work directly supports my broader goal of building efficient, AI-augmented SOC workflows (see SOC AI Workflow project).

**Status**: Actively expanding with new rules and testing scenarios.
