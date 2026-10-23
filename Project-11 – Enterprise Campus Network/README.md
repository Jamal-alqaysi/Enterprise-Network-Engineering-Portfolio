
# Project 11 – Enterprise Campus Network


![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item Value   |                                        |
| ------------ | -------------------------------------- |
| Project      | Project 11 – Enterprise Campus Network |
| Version      | v11.0                                  |
| Status       | Completed                              |
| Platform     | EVE-NG                                 |
| Vendor       | Cisco                                  |

---

## Overview

Project 11 completes the NorthStar Enterprise Network by extending the existing enterprise infrastructure with additional Layer 3, WAN, Internet, and IPv6 redundancy.

A second Headquarters edge router, HQ-RTR02, is integrated into the existing enterprise network to provide additional routing paths between the Headquarters multilayer switches, branch routers, and simulated ISP.

The existing HSRP, IPv4 and IPv6 addressing, OSPFv2, OSPFv3, DHCP, NAT/PAT, ACL, EtherChannel, Rapid PVST+, Layer 2 security, and SSH implementations from previous projects are preserved and integrated with the additional redundant infrastructure introduced in Project 11.

---

## Objectives

- Integrate HQ-RTR02 as a secondary Headquarters edge router.
- Establish redundant Layer 3 connectivity at the Headquarters.
- Provide backup WAN connections for both branch networks.
- Provide secondary Internet connectivity through ISP-RTR01.
- Configure preferred and backup OSPFv2 routing paths.
- Configure preferred and backup OSPFv3 routing paths.
- Configure NAT/PAT on the secondary Headquarters edge router.
- Introduce additional IPv4 and IPv6 transit networks.
- Configure a dedicated Linux workstation for centralized SSH management.
- Verify automatic IPv4 and IPv6 routing failover.
- Verify end-to-end IPv4 and IPv6 connectivity across the integrated enterprise network.

---

## Technologies Used

### Project 11 Technologies

- IPv4
- IPv6
- OSPFv2
- OSPFv3
- OSPF Cost Manipulation
- Layer 3 Redundancy
- WAN Redundancy
- Internet Redundancy
- NAT/PAT
- SSH
- Linux Management Workstation
- Cisco IOS
- Cisco IOL
- EVE-NG
- CLI Configuration

### Existing Enterprise Technologies Preserved

- VLAN Segmentation
- HSRP
- DHCP
- ACLs
- EtherChannel
- Rapid PVST+
- Port Security
- Sticky MAC Address Learning
- DHCP Snooping
- PortFast
- BPDU Guard
- SSH Administrative Access

---

## Project Structure

```text
Project-11-Enterprise-Campus-Network/
│
├── 01-Requirements
├── 02-Network-Design-Specification
├── 03-Implementation
├── 04-Verification
├── 05-Troubleshooting
├── 06-Lessons-Learned
├── Assets
├── Configurations
│   ├── 1. Configuration-Scope
│   ├── BR1-RTR01
│   ├── BR2-RTR01
│   ├── HQ-MLS01
│   ├── HQ-MLS02
│   ├── HQ-RTR01
│   ├── HQ-RTR02
│   ├── ISP-RTR01
│   └── Linux-mgmt01
├── Screenshots
└── README
```

---

## Enterprise Network Topology

![Enterprise Campus Network Topology](Assets/Figure%201.%20Enterprise%20Campus%20Network%20Topology.png)

The enterprise topology is expanded by introducing HQ-RTR02, additional redundant Layer 3 connections, backup branch WAN links, and a secondary Internet connection to ISP-RTR01.

A dedicated Linux management workstation, **linux-mgmt01**, is also introduced on the Management VLAN (VLAN 99) to provide centralized SSH-based administrative access to the enterprise network devices.

The final architecture provides redundant Headquarters routing paths, branch WAN connectivity, secondary Internet connectivity, additional IPv6 routing paths, and centralized network management while preserving the enterprise services implemented in previous projects.

---

## Verification Performed

The following items were successfully verified:

- OSPFv2 neighbor relationships
- OSPFv2 interface costs
- OSPFv2 route learning
- IPv4 preferred and backup WAN paths
- IPv4 WAN failover
- Secondary Internet default route
- NAT/PAT through HQ-RTR02
- OSPFv3 neighbor relationships
- OSPFv3 interface costs
- OSPFv3 route learning
- IPv6 WAN failover
- IPv6 transit interfaces
- SSH management connectivity from linux-mgmt01
- End-to-end IPv6 connectivity
- IPv4 connectivity to the verified ISP-facing destination
- Headquarters Layer 3 path failover

Controlled failure testing confirmed that OSPFv2 and OSPFv3 automatically selected the configured alternate paths when selected preferred routing paths became unavailable.

Verification screenshots are available in the **Screenshots** directory.

Previously implemented enterprise technologies were preserved as part of the cumulative architecture and were not individually re-verified in Project 11.

---
## Skills Demonstrated

- Enterprise Network Integration
- Layer 3 Redundancy
- WAN Redundancy
- Internet Redundancy
- IPv4 Routing
- IPv6 Routing
- OSPFv2
- OSPFv3
- OSPF Path Selection
- OSPF Cost Manipulation
- Routing Failover
- NAT/PAT
- Dual-Stack Networking
- SSH Network Management
- Enterprise Network Verification
- Cisco IOS CLI

---
## Result

Project 11 completed the NorthStar Enterprise Network by integrating additional Layer 3, WAN, Internet, and IPv6 redundancy into the existing enterprise architecture.

HQ-RTR02 was deployed as the secondary Headquarters edge router, while OSPFv2 and OSPFv3 provided preferred and alternate routing paths across the redundant infrastructure. Controlled failure testing demonstrated automatic IPv4 and IPv6 route convergence when selected preferred paths became unavailable, and NAT/PAT operation through HQ-RTR02 was verified during backup-path testing.

The dedicated linux-mgmt01 workstation also provided SSH-based administrative access through the Management VLAN.

The resulting NorthStar Enterprise Network provides a redundant dual-stack enterprise architecture with multiple Headquarters routing paths, branch WAN redundancy, secondary Internet connectivity, and centralized management while preserving the enterprise technologies implemented throughout the previous projects.

---
## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio