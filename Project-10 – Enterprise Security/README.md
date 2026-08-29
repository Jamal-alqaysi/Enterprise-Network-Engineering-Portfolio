
# Project 10 – Enterprise Layer 2 Security

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item | Value |
| --- | --- |
| Project | Project 10 – Enterprise Layer 2 Security |
| Version | v10.0 |
| Status | Completed |
| Platform | EVE-NG |
| Vendor | Cisco |

---

## Overview

Project 10 builds directly on the enterprise infrastructure implemented in Project 09 by introducing Layer 2 security controls across the enterprise access layer.

The existing enterprise topology, IPv4 and IPv6 addressing plans, gateway redundancy, routing architecture, and network services remain unchanged. Layer 2 security is introduced on the enterprise access switches to protect user-facing interfaces without modifying the existing enterprise architecture.

The original security plan included Port Security, Sticky MAC Address Learning, DHCP Snooping, Dynamic ARP Inspection (DAI), Storm Control, PortFast, and BPDU Guard. During implementation, DAI and Storm Control could not be reliably deployed using the Cisco IOL images available in the EVE-NG lab environment and were therefore excluded from the final configuration.

---

## Objectives

- Implement Port Security on user-facing access ports.
- Enable Sticky MAC Address Learning.
- Limit secured access ports to a single learned MAC address.
- Configure Port Security violation mode as restrict.
- Enable DHCP Snooping across the enterprise access layer.
- Configure trusted DHCP Snooping uplinks.
- Enable PortFast on user-facing access ports.
- Enable BPDU Guard to protect the spanning-tree topology.
- Evaluate Dynamic ARP Inspection (DAI) as part of the Layer 2 security design.
- Evaluate Storm Control as part of the Layer 2 security design.
- Verify the implemented Layer 2 security controls and enterprise connectivity.

---
## Technologies Used

### Final Implemented Technologies

- Port Security
- Sticky MAC Address Learning
- DHCP Snooping
- PortFast
- BPDU Guard

### Evaluated Technologies

- Dynamic ARP Inspection (DAI)
- Storm Control

### Existing Enterprise Technologies

The project operates on the cumulative enterprise infrastructure established in previous projects, including:

- HSRP
- IPv4
- IPv6
- OSPFv2
- OSPFv3
- DHCP
- NAT/PAT
- ACLs
- EtherChannel
- Rapid PVST+

### Platform

- Cisco IOS
- Cisco IOL (Layer 2)
- EVE-NG
- Cisco CLI

---
## Project Structure

```text
Project-10-Enterprise-Layer2-Security/
│
├── 01-Requirements/
├── 02-Network Design Specification/
├── 03-Implementation/
├── 04-Verification/
├── 05-Troubleshooting/
├── 06-Lessons-Learned/
├── Assets/
├── Configurations/
│   ├── 1. Configuration-Scope
│   ├── HQ-SW01
│   ├── HQ-SW02
│   ├── HQ-SW03
│   ├── BR1-SW01
│   └── BR2-SW01
├── Screenshots/
└── README.md
```

---

## Enterprise Network Topology

![Figure 1. Enterprise Security Topology](Assets/Figure%201.%20Enterprise%20Security%20Topology.png)

The physical enterprise topology remains unchanged from Project 09.

Layer 2 security is introduced at the enterprise access layer without adding new network devices or physical connections.

---

## Verification Performed

The Project 10 verification process included:

- Port Security status on HQ-SW01
- Sticky MAC Address Learning
- Port Security interface configuration
- DHCP Snooping status
- Trusted DHCP Snooping uplinks
- PortFast
- BPDU Guard
- IPv4 connectivity between the tested Headquarters and Branch networks

Dynamic ARP Inspection (DAI) and Storm Control were evaluated during implementation. DAI could not be reliably validated because the required DHCP Snooping binding information was not populated in the lab environment, while the required Storm Control functionality was unavailable on the Cisco IOL Layer 2 image.

Both features were therefore excluded from the final configuration.

Verification screenshots are available in the **Screenshots** directory.

---

## Skills Demonstrated

- Enterprise Layer 2 Security
- Port Security
- Sticky MAC Address Learning
- DHCP Snooping
- DHCP Snooping Trust Boundaries
- PortFast
- BPDU Guard
- Layer 2 Security Hardening
- Enterprise Network Verification
- Cisco IOS CLI
- EVE-NG Lab Validation
- Platform Limitation Analysis

---

## Result

Project 10 successfully strengthened the enterprise access layer by implementing Port Security, Sticky MAC Address Learning, DHCP Snooping, PortFast, and BPDU Guard across the Headquarters and Branch access switches.

Dynamic ARP Inspection and Storm Control were evaluated as part of the original security design but were excluded from the final configuration because of limitations encountered with the Cisco IOL lab environment.

IPv4 connectivity between the tested Headquarters and Branch networks was successfully verified after the supported Layer 2 security controls were applied.

---

## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio