# SOC Homelab for Blue Team Operations

## Overview
This project is a hands-on Security Operations Center (SOC) homelab designed to develop practical blue team skills, including monitoring, detection, and incident response.

The environment is built using open-source technologies and is intended to evolve over time, allowing the integration of new tools, attack simulations, and detection engineering practices.

---

## Objectives
- Develop practical blue team skills in a controlled environment
- Perform log analysis and security monitoring
- Simulate attacks and evaluate detection capabilities
- Practice incident response workflows
- Build a professional cybersecurity portfolio

---

## Lab Architecture

### Analyst Machine
- Arch Linux (Host)
- Access to Wazuh dashboard via web browser

### Virtualization Platform
- Proxmox VE (Mini PC)

### Virtual Machines

#### Wazuh Manager
- Ubuntu Server
- Central SIEM component
- Log collection, correlation, and alerting

#### Victim Machine
- Ubuntu Server
- Generates logs and simulates a production system
- Runs Wazuh agent

#### Attacker Machine
- Kali Linux (Virt-Manager)
- Used to simulate attacks and adversary behavior

---

## Network Design
The lab is designed with logical separation between attacker, victim, and monitoring components to simulate a real-world environment.

Further details are documented in:
docs/02-network-design.md


---

## Technologies
- Proxmox VE
- Wazuh SIEM
- Ubuntu Server
- Kali Linux
- Arch Linux
- KVM/QEMU

---

## Project Structure
configs/ Configuration files and system settings
diagrams/ Architecture and network diagrams
docs/ Technical documentation and setup guides
labs/ Practical attack and detection scenarios
troubleshooting/ Known issues and solutions


---

## Documentation

Follow the documentation in order:

1. Architecture overview  
   `docs/01-architecture.md`

2. Network design  
   `docs/02-network-design.md`

3. Proxmox setup  
   `docs/03-proxmox-setup.md`

4. Wazuh deployment  
   `docs/04-wazuh-setup.md`

5. Victim machine configuration  
   `docs/05-victim-machine.md`

6. Attack scenarios  
   `docs/06-attack-scenarios.md`

7. Detection and analysis  
   `docs/07-detection-and-analysis.md`

---

## Labs

The `labs/` directory contains hands-on scenarios where attacks are executed and analyzed using Wazuh.

Each lab includes:
- Attack description
- Commands used
- Logs generated
- Detection analysis

---

## Troubleshooting

Common issues and their solutions are documented in:
troubleshooting/


---

## Use Cases
- Brute force detection
- Log correlation
- File integrity monitoring
- Threat detection and analysis
- Basic threat hunting

---

## Roadmap
- Detection rule tuning
- MITRE ATT&CK mapping
- Advanced attack simulations
- Integration with additional tools (Suricata, Zeek)
- Multi-host environments
- Automated deployments

---

## Notes
This project is continuously evolving as new concepts and tools are learned and applied.
