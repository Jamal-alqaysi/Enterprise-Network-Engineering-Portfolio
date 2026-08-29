
## Overview

Project 01 establishes the initial physical and logical architecture of the NorthStar Enterprise Network.

The design follows a hierarchical enterprise model consisting of a Distribution Layer and an Access Layer. The objective is to provide a simple, scalable, and maintainable infrastructure that serves as the foundation for subsequent projects.

At this stage, all enterprise workstations operate within a single IPv4 network. Advanced technologies such as VLAN segmentation, Inter-VLAN Routing, dynamic routing, redundancy, and security are intentionally introduced in later projects.

---

## Network Topology

The enterprise network consists of one Distribution Layer multilayer switch connected to three Access Layer switches.

Six enterprise workstations are distributed across the access layer to represent users from the Human Resources, Finance, and Information Technology departments.

![Figure 1. Project 01 Core-Infrastructure-Topology](../Assets/Figure%201.%20Project%2001%20Core-Infrastructure-Topology.png)

---

## Hierarchical Network Design

The network follows a hierarchical enterprise design consisting of Distribution and Access layers.

### Distribution Layer

HQ-MLS01 provides the central switching infrastructure and aggregates the three enterprise access switches.

| Device | Role |
| --- | --- |
| HQ-MLS01 | Distribution Layer Multilayer Switch |

---

### Access Layer

The Access Layer provides network connectivity for enterprise end devices.

| Device | Role |
| --- | --- |
| HQ-SW01 | Access Layer Switch |
| HQ-SW02 | Access Layer Switch |
| HQ-SW03 | Access Layer Switch |

---

### End Devices

The enterprise workstations represent users from three business departments.

Although all workstations operate within the same IPv4 network in Project 01, the device naming convention establishes the departmental structure used throughout subsequent projects.

| Department | Devices |
| --- | --- |
| Human Resources | HR-PC01, HR-PC02 |
| Finance | FIN-PC01, FIN-PC02 |
| Information Technology | IT-PC01, IT-PC02 |

---

## Enterprise IPv4 Addressing Plan

All network management interfaces and enterprise workstations operate within the `192.168.0.0/24` network during Project 01.

| Device | IPv4 Address | Subnet Mask |
| --- | --- | --- |
| HQ-MLS01 | 192.168.0.1 | 255.255.255.0 |
| HQ-SW01 | 192.168.0.2 | 255.255.255.0 |
| HQ-SW02 | 192.168.0.3 | 255.255.255.0 |
| HQ-SW03 | 192.168.0.4 | 255.255.255.0 |
| HR-PC01 | 192.168.0.10 | 255.255.255.0 |
| HR-PC02 | 192.168.0.11 | 255.255.255.0 |
| FIN-PC01 | 192.168.0.20 | 255.255.255.0 |
| FIN-PC02 | 192.168.0.21 | 255.255.255.0 |
| IT-PC01 | 192.168.0.30 | 255.255.255.0 |
| IT-PC02 | 192.168.0.31 | 255.255.255.0 |

The access switches use `192.168.0.1` as their management default gateway.

No Layer 3 default gateway is required for workstation communication in Project 01 because all enterprise workstations operate within the same IPv4 subnet.

---

## Addressing Strategy

The IPv4 addressing scheme is structured to provide consistent host identification and simplify the transition to departmental VLANs in subsequent projects.

| Department / Function | Host Address Range |
| --- | --- |
| Infrastructure | .1 – .9 |
| Human Resources | .10 – .19 |
| Finance | .20 – .29 |
| Information Technology | .30 – .39 |

The workstation host identifiers are intentionally organized by department, providing a predictable addressing structure as the enterprise network evolves.

---

## Design Considerations

The Project 01 design intentionally maintains a simple Layer 2 architecture.

- All enterprise workstations operate within a single IPv4 subnet.
- No VLAN segmentation is implemented.
- No Inter-VLAN Routing is required.
- No dynamic or static routing is implemented.
- HQ-MLS01 operates as the central Distribution Layer switch.
- HQ-SW01, HQ-SW02, and HQ-SW03 provide Access Layer connectivity.
- SSH provides secure remote administrative access to supported network devices.

This approach establishes a stable baseline before additional enterprise networking technologies are introduced.

---

## Design Summary

Project 01 establishes the foundational architecture of the NorthStar Enterprise Network using one Distribution Layer multilayer switch, three Access Layer switches, and six enterprise workstations.

The `192.168.0.0/24` IPv4 network provides initial connectivity across the enterprise environment, while the structured device naming and addressing strategy prepares the infrastructure for future segmentation and expansion.

The resulting design provides a simple and scalable baseline for the technologies introduced throughout the subsequent NorthStar Enterprise Network projects.