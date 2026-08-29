
## Design Overview

Project 08 builds directly on the enterprise network implemented in Project 07.

The existing enterprise topology, IPv4 addressing plan, VLAN architecture, Layer 2 redundancy, OSPFv2 routing, DHCP services, NAT/PAT, and ACL security policies remain unchanged.

This project introduces IPv6 connectivity using a dual-stack architecture, allowing IPv4 and IPv6 to operate simultaneously across the enterprise network.

Each enterprise LAN and WAN segment is assigned a dedicated IPv6 /64 prefix. Dynamic IPv6 routing is provided through OSPFv3, enabling automatic route exchange between Headquarters and branch offices while preserving the existing IPv4 OSPF infrastructure.

---

## Network Topology

The physical topology remains identical to Project 07.

![Figure 1. Enterprise IPv6 Topology](../Assets/Figure%201.%20Enterprise%20IPv6%20Topology.png)

No additional network devices or physical links are introduced in this project.

---
## IPv6 Addressing Plan

| Connection / Network | IPv6 Prefix | Device / Interface | IPv6 Address |
|---|---|---|---|
| HR VLAN | `2001:DB8:10::/64` | HQ-MLS01 VLAN10 | `2001:DB8:10::1/64` |
| Finance VLAN | `2001:DB8:20::/64` | HQ-MLS01 VLAN20 | `2001:DB8:20::1/64` |
| IT VLAN | `2001:DB8:30::/64` | HQ-MLS01 VLAN30 | `2001:DB8:30::1/64` |
| Management VLAN | `2001:DB8:99::/64` | HQ-MLS01 VLAN99 | `2001:DB8:99::1/64` |
| HQ-RTR01 ↔ HQ-MLS01 | `2001:DB8:1::/64` | HQ-RTR01 Ethernet0/1 | `2001:DB8:1::1/64` |
|  |  | HQ-MLS01 Ethernet1/1 | `2001:DB8:1::2/64` |
| HQ-RTR01 ↔ BR1-RTR01 | `2001:DB8:100::/64` | HQ-RTR01 Ethernet0/0 | `2001:DB8:100::1/64` |
|  |  | BR1-RTR01 Ethernet0/0 | `2001:DB8:100::2/64` |
| HQ-RTR01 ↔ BR2-RTR01 | `2001:DB8:101::/64` | HQ-RTR01 Ethernet0/3 | `2001:DB8:101::1/64` |
|  |  | BR2-RTR01 Ethernet0/0 | `2001:DB8:101::2/64` |
| HQ-RTR01 ↔ ISP-RTR01 | `2001:DB8:102::/64` | HQ-RTR01 Ethernet1/1 | `2001:DB8:102::1/64` |
|  |  | ISP-RTR01 Ethernet0/0 | `2001:DB8:102::2/64` |
| Branch 1 LAN | `2001:DB8:40::/64` | BR1-RTR01 Ethernet0/1 | `2001:DB8:40::1/64` |
| Branch 2 LAN | `2001:DB8:50::/64` | BR2-RTR01 Ethernet0/1 | `2001:DB8:50::1/64` |

---
## Dual-Stack Design

All Layer 3 devices operate using a dual-stack architecture.

IPv4 services continue to support the existing enterprise infrastructure, while IPv6 introduces native end-to-end connectivity without affecting previously implemented services.

Both protocol stacks operate independently while sharing the same physical network infrastructure.

---
## Dynamic Routing Design

IPv4 routing continues to use OSPFv2.

IPv6 routing is introduced using OSPFv3 with a single Area 0 design across the enterprise network.

This approach maintains consistent routing behavior for both protocol versions while simplifying network administration.

---
## Design Summary

Project 08 extends the NorthStar Enterprise Network by introducing IPv6 using a dual-stack architecture.

The implementation preserves all existing IPv4 services while enabling native IPv6 communication across the enterprise through OSPFv3, providing a scalable foundation for modern enterprise networking.