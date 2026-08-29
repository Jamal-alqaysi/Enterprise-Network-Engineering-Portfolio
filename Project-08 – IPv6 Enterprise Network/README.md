
# Project 08 – IPv6 Enterprise Network

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item | Value |
|------|-------|
| Project | Project 08 – IPv6 Enterprise Network |
| Version | v8.0 |
| Status | Completed |
| Platform | EVE-NG |
| Vendor | Cisco |

---

## Overview

Project 08 builds directly on the enterprise infrastructure implemented in Project 07 by introducing IPv6 connectivity using a Dual Stack architecture.

The existing enterprise topology, IPv4 addressing plan, VLAN architecture, Layer 2 redundancy, DHCP, NAT, ACLs, and OSPFv2 configuration remain unchanged. IPv6 is deployed alongside IPv4 using OSPFv3, allowing both protocol stacks to operate simultaneously throughout the enterprise network.

---

## Objectives

- Deploy IPv6 across the enterprise network.
- Implement a Dual Stack architecture.
- Configure OSPFv3 for dynamic IPv6 routing.
- Assign IPv6 addresses to enterprise LANs and WAN links.
- Verify IPv4 and IPv6 coexistence.
- Maintain all enterprise services implemented in previous projects.

---

## Technologies Used

- Cisco IOS
- Cisco IOL (L2/L3)
- IPv4
- IPv6
- Dual Stack
- OSPFv2
- OSPFv3
- DHCP
- DHCP Relay
- NAT/PAT
- ACL
- EtherChannel
- Rapid PVST+
- EVE-NG
- CLI Configuration

---

## Project Structure

```text
Project-08-IPv6-Enterprise-Network/
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
│   ├── HQ-RTR01
│   └── ISP-RTR01
├── Screenshots
└── README.md
```

---

## Enterprise Network Topology

![Figure 1. Enterprise IPv6 Topology](Assets/Figure%201.%20Enterprise%20IPv6%20Topology.png)

The physical topology remains unchanged from Project 07.

IPv6 connectivity is introduced using a Dual Stack architecture while preserving the existing enterprise infrastructure and all previously implemented services.

---

## Verification Performed

The following items were successfully verified:

- IPv6 interface configuration
- OSPFv3 neighbor adjacency
- IPv6 routing tables
- Dual Stack functionality
- IPv6 end-to-end connectivity
- IPv4 connectivity preservation
- Enterprise IPv6 connectivity

Verification screenshots are available in the **Screenshots** directory.

---

## Skills Demonstrated

- IPv6 Deployment
- Dual Stack Implementation
- OSPFv3 Configuration
- Enterprise IPv6 Addressing
- Dynamic Routing
- DHCP Verification
- Network Troubleshooting
- Cisco IOS CLI

---

## Result

Project 08 successfully integrated IPv6 into the NorthStar Enterprise Network using a Dual Stack architecture.

The enterprise network now supports simultaneous IPv4 and IPv6 communication while preserving all previously implemented enterprise services. OSPFv3 dynamically exchanges IPv6 routes across the network, providing a scalable foundation for future enterprise expansion.

---

## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio