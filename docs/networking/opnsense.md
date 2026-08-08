# OPNsense

## Overview and Reasoning
I wanted to implement a firewall and decided on OPNsense. I had originally planned to use pfSense, however in my research I discovered that pfSense was bought by Netgate, and that turned me away.

So I landed on OPNsense. The main reason I wanted to implement a firewall was to learn how firewalls actually work on a network, while also improving the security of my homelab.

Instead of relying just on my ISP router for network security, I plan to put OPNsense in between my home network and lab environment.

For the initial implementation I am going to keep the setup simple. I do plan to use managed switches and VLANs to separate network traffic, just not yet.

## Purpose
The main purposes of OPNsense are:
- Protect my lab environment from unwanted network traffic
- Learn how firewall rules work
- Understand how NAT works
- Mess with DHCP and DNS
- Gain experience with monitoring and logging networks
- Prepare for network segmentation

## Planned Architecture

**Phase 1 — Single NIC (current plan)**
OPNsense will be deployed as a VM on the Proxmox host, initially sharing the host's single physical NIC. In this phase there is no true separation between the ISP router and the network OPNsense is meant to protect, since only one uplink exists.

**Phase 2 — WAN/LAN separation**
A second physical NIC will be added to the host so OPNsense can have a dedicated WAN interface (facing the ISP router) and a dedicated LAN interface (facing the internal network). Once this is in place, OPNsense can actually enforce a boundary between the two. Further out, I may move OPNsense off the Proxmox host entirely and onto dedicated hardware.

The planned layout (Phase 2):
```
                         Internet
                            │
                       ISP Router
                            │
                     Proxmox Host
                            │
                       OPNsense VM
                       /          \
                    WAN            LAN
                     │              │
              NIC 1 (WAN)      NIC 2 (LAN)
                                    │
                              Internal Network
```

Planned VM resources:
- CPU: 2 cores
- Memory: 4 GB
- Storage: 20–32 GB
- Network Interfaces: 2 (WAN, LAN)

This may change depending on how the firewall performs once implemented.

## Current Status

- ⏳ Second Ethernet adapter installed
- ⏳ OPNsense VM created
- ⏳ WAN configured
- ⏳ LAN configured
- ⏳ Firewall configured
- ⏳ Proxmox traffic routed through OPNsense
- ⏳ VLANs planned for future expansion

## Testing
After deployment, I plan to test the following:

### Connectivity
- Verify the LAN can reach the OPNsense gateway
- Verify the LAN can reach the internet
- Verify DNS resolution
- Verify DHCP address assignment

### Firewall
- Test allowed traffic
- Test blocked traffic
- Review firewall logs
- Verify that unexpected inbound traffic is blocked

### Troubleshooting
I will document problems encountered during deployment and the steps used to resolve them. This will include:
- Network configuration issues
- Routing problems
- DNS problems
- Firewall rule issues
- Proxmox virtual networking issues

## Future Improvements
Once the basic firewall is working, I plan to expand the network with:
- Managed Ethernet switch
- VLAN segmentation
- Dedicated management network
- Server network
- IoT network
- Guest network
- IDS/IPS
- Network monitoring
- More advanced firewall policies

The goal is to gradually move from a basic firewall deployment toward a more complete enterprise type network.
