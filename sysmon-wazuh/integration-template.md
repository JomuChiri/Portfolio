1. Title
Sysmon + Wazuh Integration

2. Objective
- What was the goal of this integration?
(e.g., “To enable centralized telemetry collection and visibility for Windows endpoint activity using Sysmon and Wazuh.”)

3. Environment Overview
- Windows Endpoint: OS version, hostname, IP.
- Sysmon Version: Include config source (e.g., Olaf Hartong’s tuned config).
- Wazuh Manager: OS, IP, dashboard access.
- Network Setup: Internal adapter, firewall rules, DNS.

4. Installation Steps
🧩 Sysmon
- Download and install Sysmon.
- Apply tuned config.
- Validate event generation (e.g., Event ID 1, 10, 11).
- Screenshot: Sysmon logs in Event Viewer.
🔗 Wazuh Agent
- Download and install Wazuh agent.
- Configure agent to connect to manager.
- Validate connection (agent status, logs flowing).
- Screenshot: Wazuh dashboard showing Sysmon events.

5. Challenges & Fixes
- Example: “Agent failed to connect due to firewall block → resolved by allowing port 1514.”
- Example: “Sysmon config too noisy → replaced with tuned config and validated reduced noise.”

6. Outcome
- Sysmon successfully logging endpoint activity.
- Wazuh agent forwarding logs to manager.
- Centralized visibility achieved.
- Screenshot: Wazuh dashboard with parsed Sysmon events.

7. Summary
“This integration demonstrates my ability to deploy endpoint telemetry tools and connect them to a SIEM for centralized visibility. I used a tuned Sysmon config to reduce noise and validated log flow into Wazuh, laying the foundation for detection engineering and incident response.”


