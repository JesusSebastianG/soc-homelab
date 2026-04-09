# Architecture Overview

## Purpose
This document defines the architecture of the SOC homelab, including system roles, responsibilities, and interaction between components.

The lab is designed to simulate a basic enterprise environment for blue team training, focusing on monitoring, detection, and incident response.

---

## Environment Overview

The lab consists of four main components:

- Monitoring system (Wazuh)
- Target system (Victim machine)
- Attacker system (Kali Linux)
- Analyst system (Host machine)

---

## Components Description

### Wazuh Manager (Ubuntu Server - VM)
- Central SIEM component
- Collects logs from monitored systems
- Performs event correlation and alerting
- Provides dashboard for analysis

---

### Victim Machine (Ubuntu Server - VM)
- Represents a production system
- Generates logs (authentication, system activity, etc.)
- Runs Wazuh agent

---

### Attacker Machine (Kali Linux - VM)
- Used to simulate attacks
- Generates malicious activity for detection testing

---

### Analyst Machine (Arch Linux - Host)
- Access point for Wazuh dashboard
- Used for monitoring and investigation

---

## Logical Flow

1. Attacker performs an action against the victim
2. Victim system generates logs
3. Wazuh agent forwards logs to the manager
4. Wazuh processes and correlates events
5. Alerts are generated
6. Analyst reviews alerts in the dashboard

---

## Design Principles

### Isolation
Each role (attacker, victim, monitoring) is logically separated to avoid interference.

### Reproducibility
The lab is designed to be rebuilt easily using documented steps.

### Scalability
The architecture allows adding more systems, tools, and detection mechanisms over time.

### Realism
The setup mimics real SOC environments at a small scale.

---

## Future Expansion

- Integration with network-based tools (Suricata, Zeek)
- Multiple victim machines
- Centralized logging pipelines
- Threat intelligence integration
