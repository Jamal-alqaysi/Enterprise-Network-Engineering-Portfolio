
# Project 03 – Network Design Specification


## Overview

Project 03 introduces Inter-VLAN Routing to the Enterprise Layer 2 foundation established in Project 02.

The physical topology, VLAN structure, trunk links, Management VLAN, Voice VLANs, and Rapid PVST+ design remain unchanged. Layer 3 communication is introduced by configuring Switch Virtual Interfaces (SVIs) on HQ-MLS01.

---

## Design Philosophy

The project follows the cumulative design model of the NorthStar Enterprise Network Engineering Portfolio.

HQ-MLS01 is selected as the Layer 3 switch responsible for departmental Inter-VLAN Routing. HQ-MLS02 remains part of the Distribution Layer topology and continues to operate within the existing Layer 2 infrastructure.

Gateway redundancy is outside the scope of Project 03.

This approach introduces Inter-VLAN Routing without redesigning the Layer 2 architecture established in Project 02.

---

## Network Topology

The physical topology remains identical to Project 02.

No additional devices or physical connections are introduced.

![Figure 3. Enterprise Inter-VLAN Routing Topology](../Assets/Figure%203.%20Enterprise%20Inter-VLAN%20Routing%20Topology.png)

---

## Layer 3 Design

HQ-MLS01 performs routing between the departmental Data VLANs.

Layer 3 switching is enabled globally, and one SVI is configured for each departmental Data VLAN. Each SVI provides the default gateway for devices within its corresponding VLAN.

HQ-MLS02 continues to operate within the existing Layer 2 design and does not provide departmental gateway services in this project.

---

## VLAN and SVI Design

| VLAN ID | VLAN Name | Network | SVI Address | Purpose |
| :--- | --- | --- | --- | --- |
| 10 | HR | 192.168.10.0/24 | 192.168.10.1/24 | HR Default Gateway |
| 20 | FINANCE | 192.168.20.0/24 | 192.168.20.1/24 | Finance Default Gateway |
| 30 | IT | 192.168.30.0/24 | 192.168.30.1/24 | IT Default Gateway |
| 99 | MANAGEMENT | 192.168.99.0/24 | 192.168.99.1/24 | Network Device Management |

Voice VLANs remain part of the Layer 2 architecture but are not routed in this project.

---

## End-Device Addressing Plan

| Device | VLAN | IP Address | Subnet Mask | Default Gateway |
| --- | ---: | --- | --- | --- |
| HR-PC01 | 10 | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 |
| HR-PC02 | 10 | 192.168.10.12 | 255.255.255.0 | 192.168.10.1 |
| FIN-PC01 | 20 | 192.168.20.11 | 255.255.255.0 | 192.168.20.1 |
| FIN-PC02 | 20 | 192.168.20.12 | 255.255.255.0 | 192.168.20.1 |
| IT-PC01 | 30 | 192.168.30.11 | 255.255.255.0 | 192.168.30.1 |
| IT-PC02 | 30 | 192.168.30.12 | 255.255.255.0 | 192.168.30.1 |

Static IPv4 addressing is used for the enterprise workstations in Project 03.

---

## Traffic Flow Design

When two devices belong to the same VLAN, traffic remains within the Layer 2 switching domain.

When devices belong to different VLANs:

1. The source device forwards the packet to its configured default gateway.
2. The corresponding SVI on HQ-MLS01 receives the packet.
3. HQ-MLS01 checks its routing table.
4. The packet is routed toward the destination VLAN.
5. The Layer 2 infrastructure delivers the frame to the destination device.

This design enables communication between departmental VLANs while maintaining their logical Layer 2 segmentation.

---

## Routing Table Design

Because the departmental networks are directly connected to HQ-MLS01 through SVIs, they appear in the IPv4 routing table as connected routes.

The routing table includes:

- `192.168.10.0/24`
- `192.168.20.0/24`
- `192.168.30.0/24`
- `192.168.99.0/24`

No static or dynamic routing protocol is required for communication between these directly connected networks.

---

## Distribution Layer Roles

### HQ-MLS01

- Operates as the Layer 3 switch for Inter-VLAN Routing.
- Hosts the departmental SVIs.
- Provides the default gateway for VLANs 10, 20, and 30.
- Routes traffic between departmental Data VLANs.
- Retains the Management VLAN 99 SVI.

### HQ-MLS02

- Remains part of the Distribution Layer topology.
- Continues Layer 2 trunking and Rapid PVST+ operation.
- Does not provide departmental gateway services in Project 03.

---

## Layer 2 Design Preservation

The following Project 02 components remain unchanged:

- VLAN assignments
- Voice VLAN assignments
- IEEE 802.1Q trunks
- Native VLAN 999
- Management VLAN 99
- Access port configuration
- Rapid PVST+
- Root bridge placement
- Redundant physical uplinks

Project 03 introduces Layer 3 functionality without redesigning the existing Layer 2 infrastructure.

---

## Design Summary

Project 03 introduces Inter-VLAN Routing by enabling Layer 3 switching and configuring departmental SVIs on HQ-MLS01.

The design allows HR, Finance, and IT devices to communicate across VLAN boundaries while preserving the Enterprise Layer 2 foundation established in Project 02.

HQ-MLS02 remains integrated into the Distribution Layer topology and continues its existing Layer 2 role.