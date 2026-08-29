
# Project 02 – Enterprise Layer 2 Foundation

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item     | Value                                      |
| -------- | ------------------------------------------ |
| Project  | Project 02 – Enterprise Layer 2 Foundation |
| Version  | v2.0                                       |
| Status   | Completed                                  |
| Platform | EVE-NG                                     |
| Vendor   | Cisco                                      |

---

## Overview

Project 02 builds directly on the infrastructure established in Project 01 by introducing the Enterprise Layer 2 Foundation of the NorthStar Enterprise Network.

The Headquarters infrastructure is expanded with a second multilayer switch and six Cisco IP Phones. Departmental Data VLANs, dedicated Voice VLANs, a Management VLAN, a Native VLAN, IEEE 802.1Q trunking, redundant Layer 2 connectivity, and Rapid PVST+ are implemented across the enterprise switching infrastructure.

The project establishes a structured and segmented Layer 2 environment while preserving the infrastructure deployed in Project 01.

---

## Objectives

- Integrate HQ-MLS02 into the Headquarters switching infrastructure.
- Add six Cisco IP Phones across the enterprise access layer.
- Configure departmental Data VLANs.
- Configure dedicated Voice VLANs.
- Configure a dedicated Management VLAN.
- Configure VLAN 999 as the Native VLAN.
- Configure IEEE 802.1Q trunk links.
- Configure Data and Voice VLAN assignments on user-facing interfaces.
- Introduce redundant Layer 2 connectivity.
- Enable Rapid PVST+.
- Configure deterministic STP root bridge selection.
- Verify VLAN segmentation, trunk operation, management connectivity, and Layer 2 operation.

---

## Technologies Used

- Cisco IOS
- Cisco IOL Layer 3
- Cisco IOL Layer 2
- VLANs
- Voice VLANs
- IEEE 802.1Q Trunking
- Management VLAN
- Native VLAN
- Rapid PVST+
- Spanning Tree Protocol
- IPv4 Management Addressing
- Cisco IP Phones
- EVE-NG
- Cisco IOS CLI
- Draw.io
- Markdown

---

## Project Structure

```text
Project-02-Enterprise-Layer-2-Foundation/
│
├── 01-Requirements
├── 02-Network-Design-Specification
├── 03-Implementation
├── 04-Verification
├── 05-Troubleshooting
├── 06-Lessons-Learned
├── Assets
├── Configurations
│   └── 1.Configuration-Scope
│   ├── HQ-MLS01
│   ├── HQ-MLS02
│   ├── HQ-SW01
│   ├── HQ-SW02
│   └── HQ-SW03
├── Screenshots
└── README
```

---

## Enterprise Network Topology

![Figure 1. Project 02 Enterprise Layer 2 Foundation Topology](Assets/Figure%201.%20Project%2002%20Enterprise%20Layer%202%20Foundation%20Topology.png)

Project 02 expands the enterprise topology established in Project 01 by introducing HQ-MLS02 as a second Distribution Layer multilayer switch and six Cisco IP Phones across the Access Layer.

The three existing access switches maintain redundant Layer 2 connectivity to the Distribution Layer, while departmental Data, Voice, and Management traffic is logically separated using VLANs.

Rapid PVST+ provides loop prevention across the redundant Layer 2 topology.

---

## VLAN Architecture

| VLAN | Name | Purpose |
| --- | --- | --- |
| 10 | HR | Human Resources Data |
| 20 | FINANCE | Finance Data |
| 30 | IT | Information Technology Data |
| 99 | MANAGEMENT | Network Device Management |
| 110 | HR-VOICE | Human Resources Voice |
| 120 | FINANCE-VOICE | Finance Voice |
| 130 | IT-VOICE | Information Technology Voice |
| 999 | NATIVE | Native VLAN for Trunk Links |

The Data and Voice VLANs provide logical separation between departmental workstation and voice traffic.

VLAN 99 provides dedicated network device management, while VLAN 999 is used as the Native VLAN across the enterprise trunk infrastructure.

---

## Management Addressing

| Device | Management IPv4 Address |
| --- | --- |
| HQ-MLS01 | 192.168.99.1/24 |
| HQ-MLS02 | 192.168.99.2/24 |
| HQ-SW01 | 192.168.99.11/24 |
| HQ-SW02 | 192.168.99.12/24 |
| HQ-SW03 | 192.168.99.13/24 |

Network device management is migrated from the Project 01 `192.168.0.0/24` network to the dedicated Management VLAN 99.

---

## Verification Performed

The following items were successfully verified:

- Updated enterprise topology
- VLAN deployment
- IEEE 802.1Q trunk operation
- Management VLAN operation
- Data and Voice VLAN assignments
- STP root bridge election
- Rapid PVST+ operation
- Management connectivity

Verification screenshots are available in the **Screenshots** directory.

---

## Skills Demonstrated

- Enterprise Layer 2 Design
- VLAN Segmentation
- Voice VLAN Configuration
- IEEE 802.1Q Trunking
- Management VLAN Deployment
- Native VLAN Configuration
- Cisco IP Phone Integration
- Redundant Layer 2 Connectivity
- Rapid PVST+
- STP Root Bridge Selection
- IPv4 Management Addressing
- Cisco IOS Configuration
- EVE-NG Network Simulation
- Network Verification
- Technical Documentation

---

## Result

Project 02 successfully established the Enterprise Layer 2 Foundation of the NorthStar Enterprise Network.

HQ-MLS02 and six Cisco IP Phones were successfully added to the infrastructure. Departmental Data VLANs, dedicated Voice VLANs, Management VLAN 99, Native VLAN 999, IEEE 802.1Q trunking, redundant Layer 2 connectivity, and Rapid PVST+ were successfully implemented and verified.

The completed Layer 2 infrastructure provides the foundation required for Inter-VLAN Routing introduced in Project 03 and for the additional enterprise technologies implemented throughout the subsequent NorthStar projects.

---

## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio