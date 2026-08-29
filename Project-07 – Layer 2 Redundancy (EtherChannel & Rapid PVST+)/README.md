
# Project 07 – Layer 2 Redundancy (EtherChannel & Rapid PVST+)

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item | Value |
|------|-------|
| Project | Project 07 – Layer 2 Redundancy (EtherChannel & Rapid PVST+) |
| Version | v7.0 |
| Status | Completed |
| Platform | EVE-NG |
| Vendor | Cisco |

---
## Overview

Project 07 enhances the Layer 2 infrastructure of the NorthStar Enterprise Network by introducing EtherChannel and Rapid PVST+.

An LACP EtherChannel is implemented between HQ-MLS01 and HQ-MLS02, combining multiple physical links into a single logical Port-Channel. The Port-Channel operates as an IEEE 802.1Q trunk and carries the required enterprise VLANs between the headquarters multilayer switches.

Rapid PVST+ provides fast spanning-tree convergence and maintains a stable, loop-free Layer 2 topology. HQ-MLS01 operates as the primary Root Bridge, while HQ-MLS02 provides the secondary Root Bridge role.

All Layer 3 routing and enterprise services implemented in previous projects remain unchanged.

---
## Objectives

- Preserve the existing enterprise topology, addressing, and services.
- Implement LACP EtherChannel between HQ-MLS01 and HQ-MLS02.
- Configure Port-Channel1 as an IEEE 802.1Q trunk.
- Preserve Native VLAN 999.
- Carry the required enterprise VLANs across the EtherChannel trunk.
- Implement Rapid PVST+.
- Configure deterministic primary and secondary Root Bridges.
- Verify EtherChannel formation and member-port status.
- Verify Port-Channel trunk operation.
- Verify spanning-tree Root Bridge election and port roles.
- Verify continued end-to-end enterprise connectivity.

---
## Technologies Used

- Cisco IOS
- Cisco IOL
- EtherChannel
- Link Aggregation Control Protocol (LACP)
- IEEE 802.1Q
- Rapid PVST+
- VLAN Trunking
- Spanning Tree Protocol
- EVE-NG
- Cisco IOS CLI

---

## Project Structure

```text
Project-07-Layer-2-Redundancy/
│
├── 01-Requirements
├── 02-Network-Design-Specification
├── 03-Implementation
├── 04-Verification
├── 05-Troubleshooting
├── 06-Lessons-Learned
├── Assets
├── Configurations
│   ├── 1.Configuration-Scope
│   ├── HQ-MLS01
│   └── HQ-MLS02
├── Screenshots
└── README
```

---

## Enterprise Network Topology

![Figure 1. Layer 2 Redundancy Topology](Assets/Figure%201.%20Layer%202%20Redundancy%20Topology.png)

The existing enterprise topology from Project 06 is preserved, with additional physical links between HQ-MLS01 and HQ-MLS02 to support the EtherChannel.

No additional network devices are introduced in this project.

---
## EtherChannel Design

| Feature           | Configuration            |
| ----------------- | ------------------------ |
| Protocol          | LACP                     |
| Connection        | HQ-MLS01 ↔ HQ-MLS02      |
| Port-Channel      | Port-Channel1            |
| Member Interfaces | Ethernet1/0, Ethernet1/2 |
| Mode              | Active                   |
| Port-Channel Type | Trunk                    |
| Encapsulation     | IEEE 802.1Q              |
| Native VLAN       | 999                      |
| Allowed VLANs     | 10,20,30,40,50,99,999    |

The two physical links operate as a single logical Layer 2 connection between the headquarters multilayer switches.

---
## Rapid PVST+ Design

| Device   | Spanning-Tree Role    |
| -------- | --------------------- |
| HQ-MLS01 | Primary Root Bridge   |
| HQ-MLS02 | Secondary Root Bridge |

Rapid PVST+ provides rapid convergence following Layer 2 topology changes while maintaining a loop-free switching environment.

The deterministic Root Bridge configuration provides predictable Layer 2 forwarding behavior.

---
## Verification Performed

The following items were successfully verified:

- Enterprise topology after Layer 2 redundancy deployment
- EtherChannel formation on HQ-MLS01
- EtherChannel formation on HQ-MLS02
- Port-Channel trunk operation
- Native VLAN configuration
- Required VLAN transport across the EtherChannel
- Root Bridge election
- Secondary Root operation
- Rapid PVST+ status
- End-to-end enterprise connectivity

Verification evidence is available in the **Screenshots** directory.

---
## Troubleshooting

Project 07 was implemented without any significant configuration or connectivity issues.

Validation confirmed successful LACP EtherChannel formation, correct Port-Channel trunk operation, expected Rapid PVST+ behavior, and continued operation of all previously implemented enterprise services.

No configuration corrections were required during the implementation.

---
## Skills Demonstrated

- Layer 2 Redundancy
- EtherChannel Configuration
- LACP
- IEEE 802.1Q Trunking
- Rapid PVST+
- Spanning-Tree Root Bridge Selection
- Port-Channel Verification
- VLAN Trunk Verification
- Layer 2 Network Validation
- Cisco IOS CLI
- EVE-NG Network Simulation
- End-to-End Connectivity Verification
- Technical Documentation

---
## Result

Project 07 successfully improved the Layer 2 resiliency of the NorthStar Enterprise Network by implementing LACP EtherChannel and Rapid PVST+.

The resulting design provides redundant Layer 2 connectivity, increased bandwidth between the headquarters multilayer switches, deterministic spanning-tree operation, and a stable loop-free switching topology while preserving the existing Layer 3 routing and enterprise services.

---
## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio