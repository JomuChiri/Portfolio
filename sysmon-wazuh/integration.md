# Sysmon + Wazuh Integration

**Part of Candor Labs** | Ongoing Project

I integrated **Sysmon** with **Wazuh** to enable rich Windows endpoint telemetry collection and centralized visibility in my home SOC lab.

## Objective

Enable high-quality endpoint logging from Windows machines and forward it to Wazuh for centralized monitoring, correlation, and future detection rule development.

## Architecture Overview

- **Windows 11 Endpoint** → Runs Sysmon + Wazuh Agent
- **Wazuh Manager** (Ubuntu) → Central SIEM for log ingestion, parsing, and alerting
- **Network Path**: Logs flow securely through the pfSense firewall (port 1514/1515 allowed)

## Key Components & Configuration

- **Sysmon**: Installed with a tuned configuration (based on SwiftOnSecurity + custom adjustments) to capture high-value events such as:
  - Process creation (Event ID 1)
  - Network connections (Event ID 3)
  - File creation / deletion (Event ID 11/23)
  - Registry modifications and driver loads
- **Wazuh Agent**: Deployed on the Windows endpoint and configured to forward Sysmon events to the manager
- **Wazuh Manager**: Custom decoders and rules created to properly parse and categorize Sysmon events

## Challenges & Solutions

| Challenge                              | Solution Implemented |
|----------------------------------------|----------------------|
| Too much noise from default Sysmon config | Switched to a tuned Sysmon configuration and fine-tuned Wazuh rules to reduce false positives |
| Wazuh Agent failing to connect to manager | Added specific firewall allow rules on pfSense for agent-manager communication (ports 1514/1515) |
| Sysmon events not appearing correctly in Wazuh dashboard | Created custom Wazuh decoders and verified field mapping |
| High volume of logs impacting performance | Implemented log filtering at the Sysmon level and tuned Wazuh agent settings |

## Results & Achievements

- Successful real-time forwarding of Sysmon events into Wazuh
- Centralized visibility of Windows endpoint activity (process, network, file, and registry events)
- Foundation laid for building custom detection rules (MITRE ATT&CK mapping)
- Improved ability to perform alert triage and correlation across endpoints

**Screenshots** (add these as you document):
- Sysmon logs in Windows Event Viewer
- Wazuh dashboard showing ingested Sysmon events
- Example alert triggered by a test activity

## Skills Demonstrated

- Endpoint telemetry engineering with Sysmon
- SIEM agent deployment and configuration
- Log parsing, decoders, and basic rule creation in Wazuh
- Troubleshooting log flow across firewall boundaries
- Understanding of event noise reduction and tuning

This integration forms the core logging backbone of my SOC lab and directly supports my detection engineering and SOC AI Workflow projects.

**Status**: Actively maintained and expanded.
