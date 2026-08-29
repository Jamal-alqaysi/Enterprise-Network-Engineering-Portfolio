
# Project 04 – Network Design Specification

## Overview

Project 04 extends the NorthStar Enterprise Network from a single-site campus into a multi-site enterprise by introducing Wide Area Network (WAN) connectivity between the Headquarters and two branch offices.

The existing Headquarters services are retained, including the Enterprise Layer 2 foundation and Inter-VLAN Routing. This project introduces a dedicated WAN edge router at the Headquarters and a router at each branch office, enabling communication between geographically separated locations through Static Routing.

The WAN architecture follows a hub-and-spoke topology, where Headquarters serves as the central site connecting Branch 1 and Branch 2. Each branch maintains its own local area network while relying on Headquarters for enterprise connectivity.

---

## Network Topology

The enterprise campus infrastructure established in Project 03 is retained. Project 04 extends the physical topology by introducing one Headquarters WAN router, two branch routers, two branch access switches, and two branch workstations.

The resulting topology follows a hub-and-spoke architecture, where Headquarters functions as the central site and Branch 1 and Branch 2 operate as remote offices.

![Figure 1. Enterprise WAN Connectivity & Static Routing](../Assets/Figure%201.%20Enterprise%20WAN%20Connectivity%20&%20Static%20Routing.png)

---

## WAN Design

The enterprise WAN consists of two independent point-to-point links connecting Headquarters with each branch office.

Each WAN connection uses a dedicated `/30` network to efficiently utilize IPv4 address space while providing point-to-point Layer 3 connectivity.

There is no direct WAN connection between Branch 1 and Branch 2. Traffic exchanged between the branches is forwarded through HQ-RTR01 at the central site.

---

## Headquarters Design

The existing Headquarters services remain operational as established in Project 03.

Existing enterprise services include:

- Enterprise Layer 2 Foundation
- Inter-VLAN Routing
- VLAN Segmentation
- IEEE 802.1Q Trunking
- Voice VLANs
- Management VLAN
- Rapid PVST+

A dedicated WAN edge router, HQ-RTR01, is introduced to provide connectivity between the Headquarters campus and the two remote branch offices.

HQ-MLS01 continues to provide Inter-VLAN Routing for the Headquarters VLANs, while HQ-RTR01 provides routing between the Headquarters campus and the branch networks.

---

## Headquarters WAN Integration

HQ-RTR01 is integrated with the Headquarters campus through a dedicated Layer 3 transit link connected to HQ-MLS01.

A separate `/30` transit network is used for this connection to maintain clear separation between enterprise routing traffic and the Management VLAN.

The Management VLAN remains dedicated to network-device administration and is not used as the transit path between the Headquarters campus and the WAN edge router.

### Active Headquarters Transit Link

| Connection | Network | HQ-RTR01 Address | HQ-MLS01 Address |
|---|---|---|---|
| HQ-RTR01 ↔ HQ-MLS01 | 10.0.0.8/30 | 10.0.0.9 | 10.0.0.10 |

The HQ-MLS01 interface connected to HQ-RTR01 operates as a Layer 3 routed interface rather than a Layer 2 switchport.

A second physical connection exists between HQ-RTR01 and HQ-MLS02. This connection is part of the topology but remains inactive and unaddressed during Project 04.

### Headquarters Router Connections

| HQ-RTR01 Interface | Connected Device | Connected Interface | Project 04 Status |
|---|---|---|---|
| Ethernet0/0 | BR1-RTR01 | Ethernet0/0 | Active |
| Ethernet0/1 | HQ-MLS01 | Ethernet1/1 | Active |
| Ethernet0/2 | HQ-MLS02 | Ethernet0/3 | Reserved |
| Ethernet0/3 | BR2-RTR01 | Ethernet0/0 | Active |

---

## Branch Design

Each branch office contains a simple LAN consisting of:

- One router
- One access switch
- One IP Phone
- One end-user workstation

Each branch router serves as the default gateway for its local LAN while providing WAN connectivity toward Headquarters.

The branch access switches provide Layer 2 connectivity between the local router and workstation. The branch routers remain responsible for all Layer 3 forwarding outside their local LANs.

### Branch Networks

| Site | LAN Network | Default Gateway |
|---|---|---|
| Branch 1 | 192.168.40.0/24 | 192.168.40.1 |
| Branch 2 | 192.168.50.0/24 | 192.168.50.1 |

---

## IP Addressing Plan

### Headquarters Networks

| Network | Purpose |
|---|---|
| 192.168.10.0/24 | HR |
| 192.168.20.0/24 | Finance |
| 192.168.30.0/24 | IT |
| 192.168.99.0/24 | Management |

### Headquarters Management Addresses

| Device | Management Interface | VLAN | IP Address |
|---|---|---:|---|
| HQ-MLS01 | VLAN 99 | 99 | 192.168.99.1/24 |
| HQ-MLS02 | VLAN 99 | 99 | 192.168.99.2/24 |
| HQ-SW01 | VLAN 99 | 99 | 192.168.99.11/24 |
| HQ-SW02 | VLAN 99 | 99 | 192.168.99.12/24 |
| HQ-SW03 | VLAN 99 | 99 | 192.168.99.13/24 |

### Branch Networks

| Network | Purpose |
|---|---|
| 192.168.40.0/24 | Branch 1 LAN |
| 192.168.50.0/24 | Branch 2 LAN |

### Branch Device Addressing

| Device | Interface | IP Address | Purpose |
|---|---|---|---|
| BR1-RTR01 | Ethernet0/1 | 192.168.40.1/24 | Branch 1 Default Gateway |
| BR1-PC01 | Ethernet0 | 192.168.40.10/24 | Branch 1 Workstation |
| BR2-RTR01 | Ethernet0/1 | 192.168.50.1/24 | Branch 2 Default Gateway |
| BR2-PC01 | Ethernet0 | 192.168.50.10/24 | Branch 2 Workstation |

### Reserved Networks

| Network | Purpose |
|---|---|
| 192.168.60.0/24 | Reserved |
| 192.168.70.0/24 | Reserved |
| 192.168.80.0/24 | Reserved |
| 192.168.90.0/24 | Reserved |

### WAN Networks

| Connection | Network | HQ Address | Branch Address |
|---|---|---|---|
| HQ-RTR01 ↔ BR1-RTR01 | 10.0.0.0/30 | 10.0.0.1 | 10.0.0.2 |
| HQ-RTR01 ↔ BR2-RTR01 | 10.0.0.4/30 | 10.0.0.5 | 10.0.0.6 |

### Headquarters Transit Network

| Connection | Network | HQ-RTR01 | HQ-MLS01 |
|---|---|---|---|
| HQ-RTR01 ↔ HQ-MLS01 | 10.0.0.8/30 | 10.0.0.9 | 10.0.0.10 |

---

## Routing Design

Headquarters functions as the central routing location for the enterprise WAN.

Static routes are configured on HQ-MLS01 and the three WAN routers to provide bidirectional communication between the Headquarters VLANs and the branch LANs.

Routing responsibilities are divided as follows:

- HQ-MLS01 continues to route traffic between the Headquarters VLANs.
- HQ-MLS01 forwards branch-bound traffic to HQ-RTR01 through the `10.0.0.8/30` transit network.
- HQ-RTR01 routes traffic between Headquarters, Branch 1, and Branch 2.
- HQ-RTR01 forwards Headquarters-bound traffic to HQ-MLS01.
- BR1-RTR01 routes traffic between the Branch 1 LAN and Headquarters through HQ-RTR01.
- BR2-RTR01 routes traffic between the Branch 2 LAN and Headquarters through HQ-RTR01.
- Traffic exchanged between Branch 1 and Branch 2 passes through HQ-RTR01.

### Routing Path

```text
HQ VLANs
    |
HQ-MLS01
    |
10.0.0.8/30 Transit Network
    |
HQ-RTR01
   / \
  /   \
BR1   BR2
```

The existing Inter-VLAN Routing configuration within Headquarters remains unchanged. Only the routed transit interface and the required Static Routes are added to HQ-MLS01 during this project.

The second connection between HQ-RTR01 and HQ-MLS02 does not participate in routing during Project 04.

---

## Design Summary

Project 04 extends the NorthStar Enterprise Network from a single-site campus into a multi-site enterprise by introducing WAN connectivity through a hub-and-spoke architecture.

The existing Headquarters services remain operational while dedicated WAN routers and point-to-point links provide connectivity between Headquarters and both branch offices.

A dedicated Layer 3 transit network connects HQ-RTR01 to HQ-MLS01 without using the Management VLAN as an enterprise routing path. Static Routing provides bidirectional communication between the Headquarters VLANs and the two branch LANs.

The additional physical connection between HQ-RTR01 and HQ-MLS02 remains inactive and unaddressed during Project 04.

The completed design establishes the WAN and Static Routing foundation for the NorthStar Enterprise Network.