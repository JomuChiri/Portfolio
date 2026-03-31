# SOC Lab Network Topology

**Part of Candor Labs** | Ongoing Project

I designed and built this isolated SOC lab to create a realistic, safe environment for practicing security operations, detection engineering, and incident response.

## Lab Architecture

![SOC Lab Network Topology](https://jomuchiri.github.io/Portfolio/images/soc-lab-network.png)

## Key Design Decisions

- **pfSense Firewall** (192.168.1.1) as the central gateway with strict egress control
- **Network Segmentation** using a dedicated LabNet (192.168.1.0/24)
- **High-risk VM Isolation**: Blocked outbound internet access for Metasploitable and Flare-VM
- **Controlled Traffic Flows**: Allowed only necessary paths for logging, DNS, and internal communication
- **Static IP Scheme**: Clean, documented addressing for all components

## Lab Components

| Component              | IP Address       | Purpose                              |
|------------------------|------------------|--------------------------------------|
| pfSense                | 192.168.1.1     | Firewall & Router                    |
| Wazuh Manager          | 192.168.1.52    | Central SIEM & Log Management        |
| AD Domain Controller   | 192.168.1.53    | Enterprise simulation                |
| Kali Linux             | 192.168.1.51    | Attack simulation                    |
| Flare-VM               | 192.168.1.55    | Malware analysis (isolated)          |
| Metasploitable         | 192.168.1.54    | Vulnerable target (isolated)         |

## Challenges & Solutions

| Challenge                              | Solution Implemented |
|----------------------------------------|----------------------|
| High-risk VMs (Metasploitable & Flare-VM) could potentially reach the internet or C2 servers | Configured strict pfSense egress rules to completely block outbound internet access from these machines |
| Wazuh agents failing to send logs across the firewall | Created specific firewall allow rules for Wazuh log collection traffic while maintaining least privilege |
| Active Directory DNS traffic being blocked unintentionally | Added targeted allow rules for DNS traffic between domain controllers |
| Managing multiple machines with changing IPs during testing | Implemented static IP assignments with clear documentation for better manageability |
| Risk of lateral movement between attack and production-like systems | Used network segmentation and strict firewall policies to isolate attack surfaces |

## What This Lab Enables

This infrastructure serves as the reliable foundation for:
- Safe attack simulation and red team exercises
- Testing custom detection rules (Sysmon + Wazuh)
- Practicing alert triage and incident response playbooks
- Developing automation scripts through the SOC AI Workflow project

**Current Status**: Actively maintained and expanded as part of Candor Labs.

**Next Steps**: Add more agents, integrate Suricata for network-level detection, and run controlled multi-stage attack scenarios.
