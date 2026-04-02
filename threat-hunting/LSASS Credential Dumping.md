# Threat Hunting: lsass Memory Dump Analysis

**Part of Candor Labs** | Ongoing Project

This case study documents a proactive threat hunting exercise I conducted in my home SOC lab, focusing on detecting credential dumping via **LSASS** process memory access — a common technique used by attackers (MITRE ATT&CK: **T1003.001**).

## Objective

Identify signs of credential theft by hunting for suspicious access to the LSASS (Local Security Authority Subsystem Service) process, which stores sensitive credentials in memory.

## Hunting Methodology

I performed the hunt using the following approach:

1. **Hypothesis**: An attacker has obtained access to the system and is attempting to dump LSASS memory to extract credentials.
2. **Data Sources**: 
   - Sysmon (Process Access events - Event ID 10)
   - Windows Security Logs
   - Wazuh for centralized visibility
3. **Tools Used**: Sysmon, Wazuh dashboard, Volatility (for offline memory analysis), and custom queries.

## Key Indicators Monitored

- Unusual process access to `lsass.exe` (especially from non-system processes)
- Processes with `SeDebugPrivilege` enabled
- Suspicious parent-child relationships (e.g., powershell.exe or cmd.exe accessing lsass.exe)
- High-volume memory reads from LSASS

## Hunt Execution & Findings

- Configured Sysmon to log detailed Process Access events targeting LSASS.
- Ran a controlled test using Mimikatz (common credential dumping tool) to simulate real attacker behavior.
- Successfully detected the malicious access in both Sysmon logs and Wazuh dashboard.
- Performed memory analysis using Volatility to confirm dumped credentials.

**Screenshot:**  
*(Add your actual hunt screenshot here)*  
![lsass Hunt Detection](../images/lsass-hunt-detection.png)

## Challenges & Solutions

| Challenge                              | Solution Implemented |
|----------------------------------------|----------------------|
| LSASS access events are very noisy     | Applied targeted filtering and focused on high-value access patterns |
| Distinguishing legitimate vs malicious access | Used process ancestry analysis and privilege checks |
| Testing in a safe environment          | Used isolated lab VMs with strict network segmentation |

## Results

- Successfully created a reusable detection rule for LSASS memory access attempts.
- Improved visibility into credential dumping techniques.
- Reduced time to detect this type of attack through proactive hunting rather than waiting for alerts.

## MITRE ATT&CK Mapping

- **T1003.001** – OS Credential Dumping: LSASS Memory
- **T1059** – Command and Scripting Interpreter

## Lessons Learned

- Proactive threat hunting significantly complements rule-based detection.
- Proper Sysmon configuration is critical for effective hunting.
- Combining endpoint telemetry (Sysmon) with centralized SIEM (Wazuh) provides powerful hunting capabilities.
- Documentation and repeatable queries are essential for future hunts.

This exercise strengthened my ability to think like an attacker and improved my detection engineering skills. It
