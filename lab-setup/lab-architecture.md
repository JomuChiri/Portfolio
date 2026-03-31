# SOC Lab Network Topology

**Ongoing Project** — Candor Labs

This is my current home SOC lab architecture designed for realistic security operations practice, detection engineering, and safe attack simulation.

## Full Lab Diagram

![SOC Lab Network Topology](https://jomuchiri.github.io/Portfolio/images/soc-lab-network.png)

> *Click on the image to enlarge if needed. The diagram shows the complete network layout, traffic flows, firewall rules, and isolation strategy.*

## Key Components

- **pfSense (192.168.1.1)** – Primary firewall and router with strict egress rules
- **Ubuntu Server – Wazuh Manager (192.168.1.52)** – Central SIEM for log collection and alerting
- **Active Directory DC01 (192.168.1.53)** – Domain controller for realistic enterprise environment simulation
- **Kali Linux (192.168.1.51)** – Attack platform
- **Flare-VM (192.168.1.55)** – Dedicated malware analysis workstation (internet blocked)
- **Metasploitable (192.168.1.54)** – Vulnerable target machine (internet blocked)

## Design Goals & Security Features

- **Network Segmentation** using LabNet (192.168.1.0/24)
- **Internet Isolation** for high-risk VMs (Metasploitable and Flare-VM have no outbound internet access)
- **Controlled Traffic** – Only necessary log forwarding, DNS, and auth traffic is allowed
- **Defense-in-Depth** through carefully defined pfSense firewall rules

## Firewall Rules Summary

- Block Flare-VM → ANY (outbound)
- Block Metasploitable → ANY (outbound)
- Allow Wazuh agent logs to manager
- Allow AD DNS traffic between domain controllers
- Allow LAN communication where required

## What I'm Currently Using This Lab For

- Testing custom detection rules (Sysmon + Wazuh)
- Practicing alert triage and incident response playbooks
- Running controlled attack simulations
- Developing SOC AI Workflow components
- Documenting real-world security operations processes

This lab serves as the foundation for all my hands-on work in Candor Labs and continues to evolve as I add new tools and scenarios.
