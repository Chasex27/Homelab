# Server Hardware

## Overview

This contains all the hardware and purpose of the physical server used for my homelab environment to be updated as things are added.

The server is used to host virtual machines, self-hosted applications, networking services, and future cybersecurity testing environments.

---

# Server Specifications

| Component | Details |
|---|---|
| System | OLD PC |
| Motherboard | RAMPAGE IV EXTREME LGA2011 |
| CPU | Intel Core i7-4770K |
| RAM | 16GB DDR3 |
| Storage | WD 2TB HDD + 500GB SSD |
| GPU | None at the moment |
| Hypervisor | Proxmox VE |

---

# Storage Configuration

## SSD

Purpose:

- Operating system storage
- Virtual machine storage
- Application storage

Drive:


WDC WDS500G2B0A-00SM50


---

## HDD

Purpose:

- Bulk storage
- Backups
- Future media/application storage

Drive:


WD2003FZWX


---

# Hardware Goals

Future improvements:

- Increase RAM capacity (up to 64gb)
- Add additional storage drives (Goal 5tb Storage
- Implement backup storage
- Add dedicated networking hardware (Small patch pannel/switch)

---

# Current Usage

The server currently hosts:

- Proxmox VE hypervisor
- Ubuntu Server virtual machine

---

# Lessons Learned

Building this server provided hands-on experience with:

- Hardware instilation
- Server deployment
- Virtualization requirements
- Storage planning
- Troubleshooting boot and installation issues
