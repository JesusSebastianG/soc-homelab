# Kali Linux Installation

This document describes how the attacker machine was deployed in the SOC homelab.

Kali Linux is used to simulate attacks against the SIEM-monitored server in order to generate security events.

---

## Virtual Machine Configuration

The Kali Linux attacker machine runs as a virtual machine managed with **KVM and Virt-Manager**.

Recommended configuration:

| Resource | Value |
|--------|------|
| OS | Kali Linux |
| RAM | 1.5 - 2 GB |
| CPU | 1 - 2 cores |
| Disk | 25 GB |
| Network | NAT (libvirt default network) |

---

## Download Kali Linux

Download the Kali Linux installer ISO from the official website.

Official source:

https://www.kali.org/get-kali/

Recommended image:

```
Kali Linux Installer (64-bit)
```

---

## Create Virtual Machine

1. Open **Virt-Manager**
2. Create a new virtual machine
3. Select the Kali Linux ISO
4. Configure resources
5. Set network interface to:

```
Virtual network: default (NAT)
```

This allows communication between the Kali machine and the Wazuh SIEM server.

---

## Kali Linux Installation

Start the installer and select:

```
Graphical Install
```

Follow the installation steps.

Example configuration:

Hostname:

```
kali-lab
```

Domain name (optional):

```
lab.local
```

Create a user account.

Example:

```
username: kali
```

---

## Software Selection

During installation, select only the required packages.

Recommended selection:

Desktop Environment:

```
XFCE
```

Collections of tools:

```
Default recommended tools
```

Avoid installing unnecessary large packages to keep the VM lightweight.

---

## Update the System

After installation, update the system.

```bash
sudo apt update
sudo apt upgrade -y
```

---

## Verify Network Connectivity

Check the IP address assigned to the machine.

```bash
ip a
```

Example output:

```
192.168.122.X
```

---

## Test Connectivity with SIEM Server

Verify connectivity with the Ubuntu Server running Wazuh.

```bash
ping 192.168.122.X
```

If the ping succeeds, both virtual machines are connected to the same network.

---

## Result

The Kali Linux machine is now ready to simulate attacks against the Wazuh SIEM server.

This machine will be used to generate malicious activity such as:

- network scanning
- brute force attacks
- malware simulation

These events will later be analyzed and detected in the Wazuh dashboard.
