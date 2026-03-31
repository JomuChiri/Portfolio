1. Title
Incident Response – Phishing Triage – [Date]

2. Objective
- What was the goal of this exercise?
(e.g., “To simulate and triage a phishing email, documenting analysis, response, and lessons learned.”)

3. Environment Overview
- Tools Used: Wazuh SIEM, Sysmon logs, email client (Outlook/Thunderbird), sandbox (e.g., Any.Run, VirusTotal).
- Lab Setup: Windows endpoint receiving test phishing email, Wazuh manager monitoring logs.
- Scenario: Simulated phishing email with suspicious attachment or link.

4. Incident Timeline
- Detection: Email received with suspicious subject line/attachment.
- Initial Triage: Identify indicators (sender domain, attachment hash, URL).
- Analysis:
- Header analysis (SPF/DKIM/DMARC checks).
- Attachment/URL sandboxing.
- Sysmon/Wazuh logs for execution attempts.
- Containment: Block sender domain, quarantine email, isolate endpoint if needed.
- Eradication: Remove malicious file, revoke compromised credentials.
- Recovery: Restore endpoint, monitor for persistence.
- Lessons Learned: Update detection rules, awareness training.

5. Evidence & Screenshots
- Email header snippet.
- Sandbox analysis screenshot.
- Wazuh alert triggered by suspicious process.
- Sysmon event log (e.g., Event ID 1 for process creation).

6. Challenges & Fixes
- Example: “Attachment bypassed AV → sandbox analysis revealed malicious macro.”
- Example: “False positive domain flagged → validated as legitimate via WHOIS.”

7. Outcome
- Phishing attempt identified and contained.
- IOC list generated (hashes, domains, IPs).
- Detection rules updated in Wazuh.
- Recruiter‑friendly screenshot of alert workflow.

8. Summary
“This case study demonstrates my ability to triage phishing emails, analyze malicious attachments, and respond effectively. I used SIEM alerts, Sysmon telemetry, and sandbox analysis to detect and contain the threat, then documented lessons learned for future prevention."
