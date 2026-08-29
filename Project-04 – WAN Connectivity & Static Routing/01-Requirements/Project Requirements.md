
## Overview

Project 04 extends the NorthStar Enterprise Network beyond the Headquarters by introducing Wide Area Network (WAN) connectivity between the Headquarters and two branch offices.

This project builds directly on the enterprise infrastructure completed in Project 03. The existing Layer 2 and Layer 3 services are retained while Static Routing is introduced to enable communication between geographically separated locations.

---

## Project Objectives

The objectives of this project are to:

- Extend the enterprise network to two remote branch offices.
- Deploy WAN links between the Headquarters and each branch.
- Configure IPv4 addressing for WAN and branch LAN networks.
- Implement Static Routing between all enterprise sites.
- Verify end-to-end connectivity across the enterprise network.
- Establish the WAN and routing foundation for subsequent projects.

---

## Existing Infrastructure

The following infrastructure is retained from Project 03:

### Headquarters

- HQ-MLS01
- HQ-MLS02
- HQ-SW01
- HQ-SW02
- HQ-SW03

Existing Enterprise Services:

- VLANs
- Inter-VLAN Routing
- IEEE 802.1Q Trunks
- Voice VLANs
- Management VLAN
- Rapid PVST+

---

## New Infrastructure

The following devices are introduced in this project:

### Headquarters

- HQ-RTR01

### Branch 1

- BR1-RTR01
- BR1-SW01
- BR1-PC01

### Branch 2

- BR2-RTR01
- BR2-SW01
- BR2-PC01

---

## Functional Requirements

The completed implementation shall provide:

- WAN connectivity between the Headquarters and Branch 1.
- WAN connectivity between the Headquarters and Branch 2.
- Local LAN connectivity within each branch.
- Static Routing between all enterprise sites.
- End-to-end communication between Headquarters and branch networks.

---

## Out of Scope

The following technologies are intentionally excluded from this project:

- Dynamic Routing (OSPF)
- Internet Connectivity
- ISP Integration
- DHCP
- DHCP Relay
- NAT
- ACL
- IPv6
- HSRP
- WAN Redundancy

---

## Expected Outcome

Upon successful completion of this project, the NorthStar Enterprise Network will operate as a multi-site enterprise connected through WAN links using Static Routing.

The completed implementation establishes the WAN and static routing foundation required for additional enterprise routing technologies introduced in subsequent projects.