# SOC Homelab – Wazuh SIEM Detection Lab

## Overview

This project documents the creation of a Security Operations Center (SOC) home lab using virtualization and open-source security tools.

The goal of this lab is to simulate cyber attacks and detect them using a SIEM platform.

This project demonstrates practical Blue Team skills including:

- SIEM deployment
- Log analysis
- Attack detection
- Security monitoring

---

## Lab Architecture

Host System:
Arch Linux

Virtualization:
KVM + libvirt + Virt-Manager

Virtual Machines:

| Machine | Role | OS |
|-------|------|------|
| soc-lab | SIEM Server | Ubuntu Server + Wazuh |
| kali-lab | Attacker | Kali Linux |

Network topology:

```
Arch Linux Host
│
├── Ubuntu Server (Wazuh SIEM)
│   └── 192.168.122.X
│
└── Kali Linux (Attacker)
    └── 192.168.122.X
```

Both machines communicate through a NAT network created by libvirt.

---

## Technologies Used

- Linux (Arch, Ubuntu Server, Kali Linux)
- KVM virtualization
- libvirt
- Virt-Manager
- Wazuh SIEM
- OpenSearch
- SSH tunneling
- Git & GitHub

---

## Lab Goals

This homelab is designed to practice the following SOC skills:

- SIEM installation and configuration
- Security monitoring
- Attack simulation
- Event analysis
- Detection engineering

---

## Planned Labs

| Lab | Description |
|----|-------------|
| Nmap Scan Detection | Detect network scanning activity |
| SSH Brute Force | Detect authentication attacks |
| Malware Simulation | Detect suspicious files |
| Custom Wazuh Rules | Create custom detection rules |

Each lab will include:

- attack simulation
- logs generated
- detection in Wazuh
- screenshots
- explanation of alerts

---

## Setup Documentation

The setup process is documented in the following directories:
setup/
networking/
troubleshooting/
labs/

---

## Networking

The lab uses a libvirt NAT network.

Example connectivity test:
ping 192.168.122.X


This confirms communication between Kali Linux and the Wazuh SIEM server.

---

## Troubleshooting

Common issues encountered during the setup:

- libvirt network "default" inactive after reboot
- virt-manager freezing due to memory saturation
- Wazuh dashboard login issues
- SSH tunneling configuration

Solutions are documented in the troubleshooting directory.

---

## Learning Outcomes

This project demonstrates skills relevant to a SOC Analyst role:

- Linux administration
- Virtualization
- Security monitoring
- SIEM configuration
- Incident detection

---

## Future Improvements

- Add more attack simulations
- Create custom Wazuh detection rules
- Integrate threat intelligence feeds
- Automate lab deployment
