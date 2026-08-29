
# Project 02 – Network Design Specification


## Overview

Project 02 establishes the Enterprise Layer 2 foundation for the NorthStar Enterprise Network Engineering Portfolio.

The infrastructure introduced in this project builds directly on Project 01 by expanding the Headquarters switching environment and introducing the Layer 2 architecture required for subsequent projects.

---

## Design Philosophy

The network follows a hierarchical enterprise design consisting of Distribution and Access layers.

A second multilayer switch is introduced to provide a scalable and redundant Layer 2 foundation. Although advanced redundancy technologies such as EtherChannel and HSRP are not implemented in this project, the infrastructure provides a foundation for additional technologies introduced in later projects.

The design emphasizes simplicity, scalability, and gradual feature integration throughout the portfolio.

---

## Network Topology

The network consists of:

- Two Distribution Layer multilayer switches
- Three Access Layer switches
- Six PCs
- Six Cisco IP Phones

Each access switch maintains redundant uplinks to both multilayer switches.

HQ-MLS02 and six Cisco IP Phones are introduced in Project 02 as part of the expanded enterprise Layer 2 infrastructure.

![Figure 1. Project 02 Enterprise Layer 2 Foundation Topology](../Assets/Figure%201.%20Project%2002%20Enterprise%20Layer%202%20Foundation%20Topology.png)

---

## Hierarchical Network Design

The network is organized into two layers:

### Distribution Layer

- HQ-MLS01
- HQ-MLS02

Responsibilities:

- VLAN distribution
- Trunk aggregation
- Layer 2 redundancy
- Spanning Tree root bridge placement

### Access Layer

- HQ-SW01
- HQ-SW02
- HQ-SW03

Responsibilities:

- End-device connectivity
- Access VLAN assignment
- Voice VLAN assignment
- Uplink connectivity to the Distribution Layer

---

## Management Addressing Plan

| Device   | Management Interface | VLAN | IP Address       |
| -------- | -------------------- | ---- | ---------------- |
| HQ-MLS01 | VLAN 99              | 99   | 192.168.99.1/24  |
| HQ-MLS02 | VLAN 99              | 99   | 192.168.99.2/24  |
| HQ-SW01  | VLAN 99              | 99   | 192.168.99.11/24 |
| HQ-SW02  | VLAN 99              | 99   | 192.168.99.12/24 |
| HQ-SW03  | VLAN 99              | 99   | 192.168.99.13/24 |

---

## VLAN Design

The enterprise network is logically segmented using dedicated VLANs for user departments, management traffic, and voice services.

| VLAN | Name | Purpose |
|------|------|---------|
| 10 | HR | User Data |
| 20 | FINANCE | User Data |
| 30 | IT | User Data |
| 99 | MANAGEMENT | Network Device Management |
| 110 | HR-VOICE | Voice Traffic |
| 120 | FINANCE-VOICE | Voice Traffic |
| 130 | IT-VOICE | Voice Traffic |
| 999 | NATIVE | Native VLAN for Trunk Links |

Logical segmentation improves network organization, scalability, and administrative simplicity.

---

## Voice VLAN Design

Each department receives a dedicated Voice VLAN to separate voice traffic from user data traffic.

Six Cisco IP Phones are introduced in Project 02 and connected through the enterprise access layer. Cisco IP Phones and workstations share the same physical access ports while remaining logically separated using dedicated Data and Voice VLANs.

IP telephony services are outside the scope of this project.

---

## Trunk Design

All switch-to-switch links operate as IEEE 802.1Q trunks.

Trunks transport all required Data VLANs, Voice VLANs, the Management VLAN, and the Native VLAN throughout the Layer 2 topology.

This design allows the required VLANs to extend across multiple enterprise switches through the trunk infrastructure.

---

## Spanning Tree Design

Rapid PVST+ is used as the Layer 2 loop prevention protocol.

Root bridge placement is intentionally controlled:

- HQ-MLS01 — Primary Root Bridge
- HQ-MLS02 — Secondary Root Bridge

The redundant topology allows Rapid PVST+ to maintain loop-free forwarding while preserving alternate Layer 2 paths.

---

## Distribution Layer Design

The Distribution Layer provides centralized Layer 2 services for the enterprise network.

Both multilayer switches aggregate the Access Layer switches and provide the Layer 2 foundation required for additional enterprise services introduced in subsequent projects.

---

## Scalability Considerations

The Project 02 architecture provides a scalable foundation for additional technologies introduced throughout the portfolio.

Subsequent projects progressively introduce technologies such as:

- Inter-VLAN Routing
- WAN Connectivity
- OSPF
- DHCP
- NAT
- ACL
- EtherChannel
- IPv6
- HSRP
- Network Security

These technologies build progressively on the NorthStar Enterprise Network as the environment evolves.

---

## Design Summary

Project 02 establishes the Enterprise Layer 2 foundation by combining VLAN segmentation, Voice VLAN implementation, IEEE 802.1Q trunking, Rapid PVST+, and redundant Distribution Layer connectivity.

The completed design provides a structured Layer 2 environment that supports the additional enterprise networking technologies introduced in subsequent NorthStar projects.