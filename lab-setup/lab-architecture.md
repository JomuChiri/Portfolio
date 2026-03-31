# SOC Lab Network Topology

**Purpose**: A realistic, segmented home SOC lab for practicing detection engineering, incident response, threat hunting, and malware analysis in a safe environment.

## Lab Architecture Overview

![SOC Lab Network Topology](https://jomuchiri.github.io/Portfolio/images/soc-lab-network.png)

### Key Components
- **pfSense** (192.168.1.1) – Firewall/Router with strict rules
- **Ubuntu Wazuh Manager** (192.168.1.52) – Central SIEM and log management
- **Active Directory DC01** (192.168.1.53) – Domain controller for realistic enterprise simulation
- **Kali Linux** (192.168.1.51) – Attack simulation platform
- **Flare-VM** (192.168.1.55) – Dedicated malware analysis workstation (no internet)
- **Metasploitable** (192.168.1.54) – Vulnerable target (isolated)

### Design Principles
- **Network Segmentation** using LabNet (192.168.1.0/24)
- **Internet Isolation** for attack and analysis VMs (Metasploitable & Flare-VM blocked)
- **Controlled Traffic Flows** – Only necessary log collection, DNS, and auth traffic allowed
- **Defense-in-Depth** – Proper firewall rules to simulate real production constraints

### Firewall Rules Summary
- Block outbound internet from analysis/attack VMs
- Allow Wazuh agent logs to manager
- Allow AD DNS traffic
- Controlled LAN communication

## What I Learned / Skills Demonstrated
- Network design and segmentation
- Secure firewall configuration with pfSense
- Safe lab isolation practices
- Integration points for Wazuh and Sysmon
- Preparation for realistic attack simulation and detection testing

This lab serves as the foundation for all my detection rules, incident response playbooks, and threat hunting exercises in Candor Labs.
