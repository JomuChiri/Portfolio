1. Title
Threat Hunting – LSASS Credential Dumping – [Date]

2. Objective
- Hypothesis: Attackers may attempt to access LSASS memory to dump credentials.
- Goal: Hunt for suspicious LSASS access events across endpoint telemetry.
- Why: Credential dumping is a high‑impact technique often used in lateral movement.

3. Environment Overview
- Endpoint: Windows 11 with Sysmon installed.
- SIEM: Wazuh manager receiving Sysmon logs.
- Telemetry: Sysmon Event ID 10 (Process Access), Event ID 1 (Process Creation).
- Tools: Wazuh queries, Sysmon config, MITRE ATT&CK mapping.

4. Hunt Workflow
a. Formulate Hypothesis:
  - “If an attacker is attempting credential dumping, we should see suspicious processes accessing lsass.exe.”
b. Define Data Sources:
  - Sysmon logs (Event ID 10).
  - Wazuh alerts for process access.
c. Query SIEM:
  - Search for Event ID 10 with TargetProcess = lsass.exe.
  - Filter by suspicious parent processes (e.g., cmd.exe, powershell.exe).
d. Analyze Results:
  - Identify legitimate vs suspicious access.
  - Note false positives (e.g., AV tools).
e. Validate Findings:
  - Simulate attack using Mimikatz in lab.
  - Confirm detection in Wazuh dashboard.
f. Document Evidence:
  - Screenshots of query results.
  - Sysmon event snippet.
  - Wazuh alert screenshot.
5. Challenges & Fixes
- Noise: Legitimate AV tools accessing LSASS.
Fix: Add exclusions for trusted processes.
- False Positives: System processes flagged.
Fix: Tune rules to focus on suspicious parent processes.

6. Outcome
- Successfully hunted for LSASS access attempts.
- Validated detection with simulated attack.
- Reduced false positives through tuning.
- IOC list generated (process names, hashes).

7. Recruiter‑Friendly Summary
“This case study demonstrates my ability to conduct hypothesis‑driven threat hunts. I investigated LSASS access attempts, validated detections with simulated attacks, and tuned rules to reduce noise. Showcasing both technical depth and operational impact.”

8. Next Steps
- Expand hunts to other credential dumping techniques (e.g., SAM database access).
- Automate queries for continuous monitoring.
- Document threat hunting playbook for reuse.


