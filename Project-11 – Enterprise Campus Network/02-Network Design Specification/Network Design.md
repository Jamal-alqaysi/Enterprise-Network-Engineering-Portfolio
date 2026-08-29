
## Design Overview

Project 11 completes the NorthStar Enterprise Network by integrating redundant Layer 3, WAN, Internet, and IPv6 paths into the existing enterprise architecture.

The existing VLAN architecture, IPv4 LAN addressing, HSRP gateway redundancy, DHCP services, ACL policies, EtherChannel, Rapid PVST+, Layer 2 security, and secure administrative access are preserved from the previous projects.

The final design introduces HQ-RTR02 as a secondary Headquarters edge router and adds alternate routing paths between the Headquarters distribution layer, Branch networks, and external network.

OSPFv2 and OSPFv3 provide dynamic routing across the redundant IPv4 and IPv6 infrastructure, with interface costs used to establish preferred and backup paths.

---

## Headquarters Redundancy Design

The Headquarters architecture uses two multilayer switches and two edge routers to provide redundant Layer 3 forwarding paths.

The HSRP gateway architecture implemented in Project 09 is preserved for the Headquarters VLANs.

HQ-MLS01 remains the preferred HSRP gateway with priority 110, while HQ-MLS02 remains the standby gateway with priority 100.

Both multilayer switches maintain routed connectivity toward both Headquarters edge routers, providing alternate Layer 3 paths through the Headquarters routing infrastructure.

---

## HSRP Design

HSRP continues to provide redundant IPv4 default gateways for the existing Headquarters VLANs.

| VLAN | HSRP Virtual Gateway | Preferred Gateway | Standby Gateway |
| --- | --- | --- | --- |
| 10 | `192.168.10.254` | HQ-MLS01 | HQ-MLS02 |
| 20 | `192.168.20.254` | HQ-MLS01 | HQ-MLS02 |
| 30 | `192.168.30.254` | HQ-MLS01 | HQ-MLS02 |
| 99 | `192.168.99.254` | HQ-MLS01 | HQ-MLS02 |

HSRP preemption allows HQ-MLS01 to resume the Active role after recovery.

The existing HSRP configuration, VLAN networks, and gateway addressing remain unchanged from Project 09.

---

## Layer 3 Redundancy Design

Additional routed connections provide redundant paths between the Headquarters multilayer switches and edge routers.

The final Layer 3 architecture provides connectivity between:

- HQ-MLS01 and HQ-RTR01
- HQ-MLS01 and HQ-RTR02
- HQ-MLS02 and HQ-RTR01
- HQ-MLS02 and HQ-RTR02

OSPF interface costs establish preferred and backup paths across the redundant routed infrastructure.

The existing routed path between HQ-MLS01 and HQ-RTR01 is preserved, while Project 11 adds the additional Layer 3 connections required to provide alternate routing paths through the Headquarters infrastructure.

If a preferred routed path becomes unavailable, OSPF can dynamically recalculate the topology and select an available alternate path.

---

## WAN Redundancy Design

The existing Branch WAN architecture is extended by adding backup connections from both Branch routers to HQ-RTR02.

Each Branch therefore maintains two routed WAN paths toward Headquarters:

- Existing path through HQ-RTR01
- Backup path through HQ-RTR02

OSPF interface costs are used to maintain the existing HQ-RTR01 paths as the preferred routes during normal operation.

The additional HQ-RTR02 WAN connections provide alternate routing paths when a preferred WAN link becomes unavailable.

---

## OSPFv2 Redundancy Design

The existing OSPFv2 routing domain is extended to include the additional Layer 3 and WAN paths introduced in Project 11.

HQ-RTR02 participates in OSPFv2 alongside the existing enterprise routing devices.

The Project 11 redundant routed connections participate in OSPF Area 0.

OSPF interface costs differentiate preferred and backup IPv4 routing paths.

The design allows OSPFv2 to dynamically converge onto an available alternate route following a preferred path failure and to return to the preferred route after the primary path is restored.

---

## Internet Redundancy Design

A second IPv4 Internet path is introduced through HQ-RTR02.

HQ-RTR01 and HQ-RTR02 maintain independent external connections to ISP-RTR01.

HQ-RTR02 uses its external connection to ISP-RTR01 as its default IPv4 route and provides NAT/PAT for the existing internal enterprise IPv4 networks.

The existing Internet and NAT/PAT configuration on HQ-RTR01 is preserved.

OSPF default-route advertisement integrates the available Internet paths with the internal enterprise routing domain.

This design provides an alternate IPv4 Internet path through HQ-RTR02 when routing converges away from the preferred path.

---

## IPv6 Redundancy Design

The existing IPv6 architecture is extended across the redundant infrastructure introduced in Project 11.

Additional IPv6 transit networks provide alternate paths through HQ-MLS02, HQ-RTR02, the Branch routers, and ISP-RTR01.

The existing IPv6 LAN prefixes remain unchanged.

### Project 11 IPv6 Transit Networks

| Connection | IPv6 Prefix | Device / Interface | IPv6 Address |
| --- | --- | --- | --- |
| HQ-RTR01 ↔ HQ-MLS02 | `2001:DB8:2::/64` | HQ-RTR01 Ethernet1/3 | `2001:DB8:2::1/64` |
| | | HQ-MLS02 Ethernet1/3 | `2001:DB8:2::2/64` |
| HQ-RTR02 ↔ HQ-MLS02 | `2001:DB8:3::/64` | HQ-RTR02 Ethernet0/0 | `2001:DB8:3::1/64` |
| | | HQ-MLS02 Ethernet0/3 | `2001:DB8:3::2/64` |
| HQ-RTR02 ↔ HQ-MLS01 | `2001:DB8:4::/64` | HQ-RTR02 Ethernet0/2 | `2001:DB8:4::1/64` |
| | | HQ-MLS01 Ethernet0/0 | `2001:DB8:4::2/64` |
| HQ-RTR02 ↔ BR1-RTR01 | `2001:DB8:103::/64` | HQ-RTR02 Ethernet0/1 | `2001:DB8:103::1/64` |
| | | BR1-RTR01 Ethernet0/2 | `2001:DB8:103::2/64` |
| HQ-RTR02 ↔ BR2-RTR01 | `2001:DB8:104::/64` | HQ-RTR02 Ethernet0/3 | `2001:DB8:104::1/64` |
| | | BR2-RTR01 Ethernet0/2 | `2001:DB8:104::2/64` |
| HQ-RTR02 ↔ ISP-RTR01 | `2001:DB8:105::/64` | HQ-RTR02 Ethernet1/1 | `2001:DB8:105::1/64` |
| | | ISP-RTR01 Ethernet0/1 | `2001:DB8:105::2/64` |

The existing IPv6 networks implemented in previous projects are preserved without modification.

---

## OSPFv3 Redundancy Design

OSPFv3 is extended across the new IPv6 transit networks introduced in Project 11.

HQ-RTR02 participates in the OSPFv3 routing domain using router ID:

`7.7.7.7`

OSPFv3 adjacencies are designed across the additional Headquarters, Branch WAN, and ISP paths.

Interface costs differentiate preferred and backup IPv6 routing paths across the redundant infrastructure.

The additional path between HQ-RTR01 and HQ-MLS02 also participates in OSPFv3, completing the redundant IPv6 routing architecture at Headquarters.

If a preferred IPv6 routing path becomes unavailable, OSPFv3 can dynamically converge onto an available alternate path.

---

## Management Design

A dedicated Linux management workstation, `linux-mgmt01`, is added to the existing Management VLAN.

The workstation provides a centralized endpoint for SSH-based administrative access and verification of enterprise network devices.

The workstation uses:

- IPv4 address: `192.168.99.10/24`
- Default gateway: `192.168.99.254`

The existing Management VLAN architecture and HSRP virtual gateway remain unchanged.

---

## Existing Enterprise Services

The following technologies implemented in previous projects are preserved as part of the final enterprise architecture:

- VLAN segmentation
- HSRP gateway redundancy
- DHCP
- ACLs
- EtherChannel
- Rapid PVST+
- Port Security
- Sticky MAC Address Learning
- DHCP Snooping
- PortFast
- BPDU Guard
- SSH administrative access

Project 11 does not redesign these services. The project integrates them with the additional Layer 3, WAN, Internet, IPv4, and IPv6 routing infrastructure introduced in the final architecture.

---

## Network Topology

Project 11 uses the final redundant NorthStar Enterprise Network topology.

The existing enterprise topology is extended with the additional Headquarters routing, Branch WAN, Internet, and IPv6 paths required for the final integration.

A dedicated Linux management workstation is also included in the Management VLAN for centralized SSH-based administrative verification.

![Figure 1. Enterprise Campus Network Topology](../Assets/Figure%201.%20Enterprise%20Campus%20Network%20Topology.png)