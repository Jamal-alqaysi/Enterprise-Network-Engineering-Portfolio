
## Overview

Project 05 builds directly on the enterprise WAN infrastructure implemented in Project 04.

The physical topology, IPv4 addressing plan, WAN links, VLAN architecture, and Inter-VLAN Routing are retained. This project replaces Static Routing with Open Shortest Path First (OSPF), allowing the participating Layer 3 devices to dynamically exchange IPv4 routing information.

The network continues to follow the existing hub-and-spoke architecture, with Headquarters serving as the central routing location connecting Branch 1 and Branch 2.

---

## Network Topology

The physical topology remains identical to Project 04.

![Figure 1. Enterprise OSPF Topology](../Assets/Figure%201.%20Enterprise%20OSPF%20Topology.png)

No additional network devices or physical connections are introduced in this project.

---

## OSPF Design

A single OSPF routing domain is implemented across the enterprise WAN.

All participating Layer 3 devices exchange routing information dynamically using OSPF Area 0.

### OSPF Characteristics

| Item | Value |
|------|-------|
| Routing Protocol | OSPFv2 |
| OSPF Process ID | 1 |
| OSPF Area | Area 0 |
| Design | Single Area |
| IP Version | IPv4 |

---

## Participating Devices

The following devices participate in OSPF routing:

| Device | Role |
|---------|------|
| HQ-MLS01 | Headquarters Layer 3 Switch |
| HQ-RTR01 | Headquarters WAN Router |
| BR1-RTR01 | Branch 1 Router |
| BR2-RTR01 | Branch 2 Router |

The remaining Layer 2 switches do not participate in OSPF.

---

## Network Advertisement

The existing enterprise IPv4 networks are advertised through OSPF according to the role of each participating Layer 3 device.

### Headquarters Networks

| Network | Purpose | Advertised By |
|---------|---------|---------------|
| 192.168.10.0/24 | HR | HQ-MLS01 |
| 192.168.20.0/24 | Finance | HQ-MLS01 |
| 192.168.30.0/24 | IT | HQ-MLS01 |
| 192.168.99.0/24 | Management | HQ-MLS01 |

### Branch Networks

| Network | Purpose | Advertised By |
|---------|---------|---------------|
| 192.168.40.0/24 | Branch 1 LAN | BR1-RTR01 |
| 192.168.50.0/24 | Branch 2 LAN | BR2-RTR01 |

### Transit Network

| Network | Purpose | Participating Devices |
|---------|---------|-----------------------|
| 10.0.0.8/30 | HQ-MLS01 ↔ HQ-RTR01 | HQ-MLS01, HQ-RTR01 |

### WAN Networks

| Connection | Network | Participating Devices |
|------------|---------|-----------------------|
| HQ-RTR01 ↔ BR1-RTR01 | 10.0.0.0/30 | HQ-RTR01, BR1-RTR01 |
| HQ-RTR01 ↔ BR2-RTR01 | 10.0.0.4/30 | HQ-RTR01, BR2-RTR01 |

---

## OSPF Advertisement Design

The OSPF advertisements implemented on each participating device are:

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

## Routing Design

The Static Routes configured in Project 04 are removed from all participating Layer 3 devices.

OSPF dynamically exchanges routing information between Headquarters and both branch offices, eliminating the manually configured Static Routes while preserving the existing enterprise topology and IPv4 addressing plan.

HQ-MLS01 continues to provide Inter-VLAN Routing for the Headquarters campus and participates in OSPF through the existing Layer 3 transit connection to HQ-RTR01.

HQ-RTR01 maintains its central role within the hub-and-spoke WAN topology and forms the routing path between Headquarters and both branch offices.

BR1-RTR01 and BR2-RTR01 advertise their respective local LAN networks while participating in OSPF across their existing WAN connections to Headquarters.

---

## Design Summary

Project 05 replaces the Static Routing implementation from Project 04 with single-area OSPFv2.

The existing physical topology and IPv4 addressing plan remain unchanged. HQ-MLS01, HQ-RTR01, BR1-RTR01, and BR2-RTR01 participate in OSPF Area 0 and dynamically exchange the enterprise IPv4 routing information required for end-to-end connectivity.

The completed design establishes dynamic IPv4 routing across the existing NorthStar Enterprise WAN.