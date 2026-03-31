1. Title
Forensics – Memory Analysis – [Date]

2. Objective
- Goal: Investigate a captured memory image for signs of malware or credential theft.
- Why: Memory analysis reveals in‑memory artifacts (processes, handles, network connections) that may not persist on disk.
- Scenario: Simulated malware execution on a Windows endpoint, followed by memory capture.

3. Environment Overview
- Endpoint: Windows 11 VM with Sysmon logging.
- Tools:
- Memory capture tool (e.g., DumpIt, FTK Imager).
- Analysis framework (Volatility, Rekall).
- SIEM (Wazuh) for correlated logs.
- Data: Memory image file (.raw or .mem).

4. Acquisition
- Capture memory image from endpoint after simulated attack.
- Document acquisition method (tool used, command executed).
- Validate integrity (hash the image file).
- Store securely for analysis.

5. Analysis Workflow
🔍 Process Analysis
- Run Volatility plugin: pslist, pstree.
- Identify suspicious processes (e.g., mimikatz.exe, injected powershell.exe).
- Screenshot: process tree output.
🔗 Network Connections
- Run netscan.
- Identify unusual outbound connections.
- Document IPs/domains.
🧩 DLL & Handles
- Run dlllist and handles.
- Look for injected DLLs or suspicious handles to lsass.exe.
📜 Command History
- Run cmdscan or consoles.
- Extract attacker commands executed in memory.

6. Challenges & Fixes
- Large memory image size → chunked analysis.
- False positives (legitimate system processes flagged).
- Fix: Cross‑reference with Sysmon/Wazuh logs for validation.

7. Outcome
- Identified suspicious process accessing LSASS.
- Found malicious DLL injection.
- Extracted IOC list (process names, hashes, IPs).
- Correlated findings with SIEM alerts.

8. Recruiter‑Friendly Summary
“This case study demonstrates my ability to perform memory forensics, capturing and analyzing volatile artifacts to detect credential dumping and malware activity. I used Volatility to identify suspicious processes and correlated findings with SIEM telemetry, showing both technical depth and investigative rigor.”
