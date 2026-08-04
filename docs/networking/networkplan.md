# Planned Network Layout

## Overview

This diagram represents the target architecture for my homelab as it continues to grow. While some components are still in the planning phase, the overall goal is to build a secure and scalable environment for learning networking, virtualization, and systems administration.

Current infrastructure includes a Proxmox server with Tailscale configured for secure remote access. Future upgrades will focus on network segmentation, firewall management, and enterprise-style networking.

## Planned Network Topology

```text Internet
                                 │
                               Router
                                 │
                     OPNsense Firewall (Planned)
                                 │
                  Managed Network Switch (Planned)
                                 │
                           Proxmox Host
                     (Current Tailscale Node) ◄────── Encrypted Tailscale Tunnel ────── Personal Devices
                                 │
        ┌────────────────────────┼────────────────────────┐
        │                        │                        │
 Ubuntu Server VM          Windows VM              (Future VMs/LXCs)
        │
        └── Docker Services
                │
                └── Future Self-hosted Applications
```

## Planned Infrastructure

### OPNsense *(Planned)*
OPNsense will become the primary firewall and router for my homelab. Once deployed, it will replace my ISP router's networking responsibilities and provide a dedicated platform for learning enterprise networking concepts.

What OPNsense will do:
- Firewall rule management
- Network Address Translation (NAT)
- DHCP services
- VLAN routing and segmentation
- Site-to-site VPN, to complement (not replace) Tailscale for device-level remote access
- Traffic monitoring and logging

Implementing OPNsense will give me experience with enterprise firewall management, network security, and routing.

---

### Managed Switch *(Planned)*
A managed switch will be added to support VLANs and improve network organization as the homelab expands.

Planned VLANs include:
- **Management** – Infrastructure devices such as Proxmox and future networking equipment.
- **Servers** – Virtual machines and self-hosted services.
- **Personal Devices** – Desktops, laptops, and mobile devices.
- **IoT** – Smart home devices and other network equipment.
- **Guest** – Isolated network for guest devices.

The managed switch will allow me to practice network segmentation, VLAN configuration, and inter-VLAN routing through OPNsense.

---

### Future Expansion
As the homelab continues to grow, I plan to add:
- Reverse proxy for internal services
- Centralized monitoring and logging
- Automated backups
- Additional self-hosted applications
- Infrastructure documentation and network diagrams
- Security hardening and access control improvements
