# KVM Installation on Arch Linux

This document explains how the virtualization environment was prepared on the host machine to run the SOC homelab.

The host system used is **Arch Linux**, and virtualization is handled using **KVM, libvirt, and Virt-Manager**.

---

## Host System

Operating System:

Arch Linux

Virtualization stack:

- KVM
- QEMU
- libvirt
- Virt-Manager

---

## Verify CPU Virtualization Support

First, verify that the CPU supports hardware virtualization.

```bash
lscpu | grep Virtualization
```

Expected output:

```
Virtualization: VT-x
```

Load KVM modules:

```bash
lsmod | grep kvm
```

Expected modules:

```
kvm_intel
kvm
```

---

## Install Virtualization Packages

Install the required virtualization tools.

```bash
sudo pacman -S qemu-full virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat libvirt
```

These packages provide:

- QEMU → virtual machine emulator  
- libvirt → virtualization management service  
- Virt-Manager → graphical VM manager  
- dnsmasq → DHCP service for virtual networks  

---

## Enable libvirt Service

Start and enable the libvirt service.

```bash
sudo systemctl enable --now libvirtd
```

Verify the service is running:

```bash
sudo systemctl status libvirtd
```

---

## Add User to libvirt Group

Allow the current user to manage virtual machines without root privileges.

```bash
sudo usermod -aG libvirt $USER
```

Log out and log back in to apply the changes.

---

## Verify Virtualization

List available virtual machines:

```bash
virsh list --all
```

Launch the virtualization manager:

```bash
virt-manager
```

---

## Troubleshooting

### Network "default" inactive after reboot

After rebooting the host, the virtual network may appear inactive.

Example error:

```
Network 'default' is not active
```

Check network status:

```bash
sudo virsh net-list --all
```

Start the default network:

```bash
sudo virsh net-start default
```

Enable autostart:

```bash
sudo virsh net-autostart default
```

Verify again:

```bash
sudo virsh net-list --all
```

Expected output:

```
default   active   yes
```

---

## Result

The host system is now ready to run the SOC homelab virtual machines using KVM.
