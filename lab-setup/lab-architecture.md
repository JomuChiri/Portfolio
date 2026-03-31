# SOC Lab Network Topology

**Part of Candor Labs**

This is my personal SOC lab environment designed for hands-on security operations practice.

## Full Network Diagram

![SOC Lab Network Topology](https://jomuchiri.github.io/Portfolio/images/soc-lab-network.png)

## Networking & Infrastructure Highlights

- **Firewall Implementation**: Deployed and configured pfSense as the central firewall and router (192.168.1.1)
- **Network Segmentation**: Created a dedicated LabNet (192.168.1.0/24) to separate different security zones
- **Egress Control & Isolation**: 
  - Blocked outbound internet access for high-risk VMs (Metasploitable and Flare-VM)
  - Prevented potential command-and-control or data exfiltration from attack/analysis machines
- **Static IP Management**: Planned and assigned clean, documented IP addresses for all lab components
- **Traffic Flow Design**: Defined clear rules for:
  - Normal LAN traffic
  - Log collection paths
  - DNS and authentication traffic
  - Blocked unwanted outbound connections

## Lab Components

| Component              | IP Address       | Role                              |
|------------------------|------------------|-----------------------------------|
| pfSense Firewall       | 192.168.1.1     | Firewall / Router                 |
| Wazuh Manager          | 192.168.1.52    | SIEM Server                       |
| AD DC01                | 192.168.1.53    | Active Directory Domain Controller|
| Kali Linux             | 192.168.1.51    | Attack Simulation                 |
| Flare-VM               | 192.168.1.55    | Malware Analysis Workstation      |
| Metasploitable         | 192.168.1.54    | Vulnerable Target                 |

## Key Takeaways

This lab demonstrates practical networking knowledge applied to security environments, including:
- Secure firewall rule configuration
- Network segmentation best practices
- Controlled traffic management
- Safe isolation of attack surfaces

The infrastructure serves as the foundation for detection engineering and SIEM integration (covered in the Sysmon + Wazuh section).

**Status**: Ongoing — continuously expanded as part of Candor Labs.
