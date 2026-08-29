
# Project 05 – Dynamic Routing Implementation (OSPF)

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item | Value |
|------|-------|
| Project | Project 05 – Dynamic Routing Implementation (OSPF) |
| Version | v5.0 |
| Status | Completed |
| Platform | EVE-NG |
| Vendor | Cisco |

---

## Overview

Project 05 replaces the Static Routing implementation from Project 04 with Open Shortest Path First (OSPF).

The existing physical topology, IPv4 addressing plan, VLAN architecture, and WAN infrastructure are retained. OSPF enables the participating Layer 3 devices to dynamically exchange IPv4 routing information between Headquarters and both branch offices.

---

## Objectives

- Preserve the existing Project 04 enterprise topology.
- Remove the previously configured Static Routes.
- Implement OSPFv2 across the enterprise WAN.
- Use a single OSPF routing area.
- Advertise the existing Headquarters, branch, transit, and WAN networks.
- Establish OSPF neighbor adjacencies.
- Verify dynamic route learning.
- Maintain end-to-end enterprise connectivity.

---

## Technologies Used

- Cisco IOS
- Cisco IOL
- OSPFv2
- Single-Area OSPF
- OSPF Area 0
- Dynamic IPv4 Routing
- IPv4
- Layer 3 Routing
- EVE-NG
- Cisco IOS CLI

---

## Project Structure

```text
Project-05-Dynamic-Routing-Implementation-OSPF/
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
│   ├── BR1-RTR01
│   ├── BR2-RTR01
│   ├── HQ-MLS01
│   └── HQ-RTR01
├── Screenshots
└── README
```

---

## Enterprise Network Topology

![Figure 1. Enterprise OSPF Topology](Assets/Figure%201.%20Enterprise%20OSPF%20Topology.png)

The physical topology remains identical to Project 04.

No additional network devices or physical connections are introduced in Project 05. The existing Headquarters and branch infrastructure is retained while OSPF replaces the previous Static Routing implementation.

---

## OSPF Design

Project 05 implements OSPFv2 as a single-area routing domain using Area 0.

| Item | Value |
|------|-------|
| OSPF Process ID | 1 |
| OSPF Area | Area 0 |
| OSPF Design | Single Area |
| IP Version | IPv4 |

The following Layer 3 devices participate in OSPF:

- HQ-MLS01
- HQ-RTR01
- BR1-RTR01
- BR2-RTR01

---

## OSPF Network Advertisements

### HQ-MLS01

- `192.168.10.0/24`
- `192.168.20.0/24`
- `192.168.30.0/24`
- `192.168.99.0/24`
- `10.0.0.8/30`

### HQ-RTR01

- `10.0.0.0/30`
- `10.0.0.4/30`
- `10.0.0.8/30`

### BR1-RTR01

- `10.0.0.0/30`
- `192.168.40.0/24`

### BR2-RTR01

- `10.0.0.4/30`
- `192.168.50.0/24`

All advertised networks participate in OSPF Area 0.

---

## Routing Transition

The Static Routes configured in Project 04 are removed from the participating Layer 3 devices.

OSPF dynamically exchanges routing information across the existing WAN infrastructure while preserving the existing IPv4 addressing plan and hub-and-spoke topology.

---

## Verification Performed

The following items were successfully verified:

- OSPF neighbor adjacencies
- Dynamic OSPF route learning
- Headquarters routing tables
- Branch routing tables
- OSPF Link-State Database
- Headquarters-to-Branch connectivity
- Branch-to-Branch connectivity

Verification screenshots are available in the **Screenshots** directory.

---

## Skills Demonstrated

- OSPFv2 Configuration
- Single-Area OSPF
- Dynamic Routing
- OSPF Neighbor Verification
- Dynamic Route Verification
- Link-State Database Verification
- IPv4 Routing
- Enterprise WAN Routing
- Cisco IOS CLI
- Network Verification
- EVE-NG Network Simulation
- Technical Documentation

---

## Result

Project 05 successfully replaced Static Routing with OSPF across the NorthStar Enterprise Network.

HQ-MLS01, HQ-RTR01, BR1-RTR01, and BR2-RTR01 dynamically exchange IPv4 routing information through OSPF Area 0 while preserving the existing enterprise topology and addressing plan.

OSPF neighbor adjacencies, dynamically learned routes, the Link-State Database, and end-to-end enterprise connectivity were successfully verified.

---

## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio