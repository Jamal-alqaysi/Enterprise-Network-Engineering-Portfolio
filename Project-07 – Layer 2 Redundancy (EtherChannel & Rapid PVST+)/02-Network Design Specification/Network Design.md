
## Design Overview

Project 07 builds directly on the enterprise network implemented in Project 06.

The existing enterprise topology, IPv4 addressing plan, VLAN architecture, Layer 3 routing, DHCP services, NAT/PAT, and ACL security policies remain unchanged.

This project enhances the Layer 2 infrastructure by introducing an EtherChannel between the headquarters multilayer switches using LACP. The EtherChannel operates as a single IEEE 802.1Q trunk, providing increased bandwidth and link redundancy while simplifying Layer 2 forwarding.

Rapid PVST+ is deployed to provide fast spanning-tree convergence and maintain a loop-free switching topology. HQ-MLS01 is configured as the Root Bridge for all enterprise VLANs to ensure predictable traffic forwarding.

---

## Network Topology

The existing enterprise topology from Project 06 is preserved, with additional physical links between HQ-MLS01 and HQ-MLS02 to support the EtherChannel.

![Figure 1. Layer 2 Redundancy Topology](../Assets/Figure%201.%20Layer%202%20Redundancy%20Topology.png)

No additional network devices are introduced in this project.

The only physical enhancement is the implementation of an EtherChannel between HQ-MLS01 and HQ-MLS02.

---

## Layer 2 Redundancy Design

| Feature | Configuration |
|----------|---------------|
| EtherChannel Protocol | LACP (IEEE 802.3ad) |
| EtherChannel Link | HQ-MLS01 ↔ HQ-MLS02 |
| Port-Channel Mode | Trunk |
| Encapsulation | IEEE 802.1Q |
| Native VLAN | 999 |
| Allowed VLANs | 10,20,30,40,50,99,999 |

---

## Spanning Tree Design

| Feature | Value |
|----------|-------|
| Spanning Tree Mode | Rapid PVST+ |
| Root Bridge | HQ-MLS01 |
| Secondary Root | HQ-MLS02 |

Rapid PVST+ provides rapid convergence following Layer 2 topology changes while preventing switching loops across the enterprise campus.

---

## Design Summary

Project 07 introduces Layer 2 redundancy by combining LACP EtherChannel with Rapid PVST+.

The resulting design increases link availability, improves bandwidth utilization between the headquarters multilayer switches, and maintains a stable, loop-free Layer 2 topology without modifying any services implemented in previous projects.