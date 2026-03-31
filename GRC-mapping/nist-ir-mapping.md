GRC Case Study – NIST IR Mapping
1. Title
GRC Compliance – NIST Incident Response Mapping – [Date]

2. Objective
- Goal: Map SOC incident response workflows to the NIST IR lifecycle.
- Why: Demonstrates compliance awareness and ability to align technical work with governance frameworks.
- Scenario: Use a phishing triage or brute force incident as the example.

3. Environment Overview
- SOC Lab Tools: Wazuh SIEM, Sysmon telemetry, incident response playbooks.
- Framework: NIST SP 800‑61 Rev. 2 (Computer Security Incident Handling Guide).
- Data Sources: Case studies (phishing triage, brute force, malware).

4. Lifecycle Mapping
🟧 Preparation
- SOC lab built with Wazuh + Sysmon.
- Playbooks documented (phishing, brute force, malware).
- Escalation paths defined.
- Awareness training simulated.
🟩 Detection
- Alerts triggered in Wazuh (e.g., suspicious email, brute force login).
- Sysmon logs correlated.
- Initial triage performed.
- Decision: true positive vs false positive.
🟥 Containment
- Isolate affected endpoint.
- Block malicious domain/IP.
- Quarantine suspicious email/file.
- Disable compromised account.
🟦 Eradication
- Remove malicious files or registry entries.
- Patch exploited vulnerabilities.
- Revoke compromised credentials.
- Validate eradication with endpoint scans.
🟨 Recovery
- Restore systems from backups if needed.
- Reconnect endpoints to network.
- Monitor for persistence or re‑infection.
- Validate normal operations.
🟪 Lessons Learned
- Document incident timeline and actions.
- Update detection rules and playbooks.
- Share IOC list with threat intel feeds.
- Draft executive summary for management.
- Feed improvements back into Preparation phase.

5. Evidence & Screenshots
- Wazuh alert screenshot.
- Sysmon event snippet.
- Playbook excerpt showing mapped steps.
- IOC list table.

6. Outcome
- Incident response workflow fully mapped to NIST lifecycle.
- Demonstrated compliance alignment.
- Recruiter‑friendly artifact showing both technical and governance maturity.

7. Recruiter‑Friendly Summary
“This case study demonstrates my ability to align SOC incident response workflows with the NIST Incident Response Lifecycle. I mapped detection, containment, eradication, recovery, and lessons learned to compliance standards, showing both technical depth and governance awareness.”
