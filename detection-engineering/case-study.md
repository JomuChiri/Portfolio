1. Title
Detection Engineering – [Technique Name]
(e.g., “Credential Dumping via LSASS Access – March 2026”)

2. Objective
- What technique are you detecting?
(e.g., “Detect unauthorized access to LSASS memory for credential dumping.”)
- Why is it important?
(e.g., “This technique is used by attackers to extract plaintext credentials from memory.”)

3. Environment & Tools
- Endpoint: Windows 11 with Sysmon installed.
- SIEM: Wazuh manager receiving logs.
- Config Source: Olaf Hartong’s Sysmon config (tuned).
- Rule Engine: Wazuh ruleset or custom rule.

4. Detection Logic
- MITRE ATT&CK Mapping: T1003.001 – LSASS Memory
- Sysmon Event IDs Used:
- Event ID 10 (Process Access)
- Event ID 1 (Process Creation)
- Rule Snippet:
        <rule id="100001" level="10">
          <if_sid>576</if_sid>
          <field name="event_id">10</field>
          <field name="target_process">lsass.exe</field>
          <description>Possible credential dumping via LSASS access</description>
        </rule>
        
5. Simulation & Validation
- Simulate attack using Mimikatz or similar tool.
- Observe Sysmon logs → confirm Wazuh alert.
- Screenshot: Wazuh dashboard showing triggered alert.

6. Noise Reduction & Tuning
- Identify false positives (e.g., legitimate AV scans).
- Add exclusions or context (e.g., trusted signer, known process).
- Document before/after alert volume.

7. Outcome
- Successfully detected credential dumping attempt.
- Alert triggered in Wazuh with clear context.
- Reduced noise through rule tuning.

8. Summary
“This case study demonstrates my ability to engineer precise detection rules for real-world attack techniques. I mapped the detection to MITRE ATT&CK, tuned Sysmon and Wazuh rules, and validated alerts through simulation—showing both technical depth and operational impact.”
