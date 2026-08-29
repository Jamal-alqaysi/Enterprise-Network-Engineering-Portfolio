
## Implementation Overview

Project 11 was implemented by extending the existing NorthStar Enterprise Network with redundant Layer 3, WAN, Internet, and IPv6 paths.

The existing enterprise services and configurations from previous projects were preserved. Implementation focused on the additional components and routing paths required to complete the final redundant architecture.

The deployment was completed in stages while integrating the additional redundant infrastructure with the existing enterprise network.

---

## Headquarters Redundancy Implementation

HQ-RTR02 was introduced into the Headquarters infrastructure as the second enterprise edge router.

Additional routed connections were established between the Headquarters multilayer switches and edge routers to provide multiple Layer 3 paths through the Headquarters infrastructure.

The existing HSRP gateway architecture implemented in Project 09 was preserved as part of the final integrated design.

HQ-MLS01 remained the preferred HSRP gateway with priority 110, while HQ-MLS02 remained the standby gateway with priority 100 for the Headquarters VLANs.

The existing HSRP preemption behavior was also preserved, allowing HQ-MLS01 to resume the Active role after recovery.

---

## Layer 3 Routing Redundancy Implementation

The existing OSPFv2 routing domain was extended across the additional routed connections introduced in Project 11.

HQ-RTR02 was added to the OSPFv2 routing topology, and the additional Headquarters and WAN interfaces were integrated into OSPF Area 0.

OSPF interface costs were applied to differentiate preferred and backup routing paths.

The existing routing paths through HQ-RTR01 were maintained as the preferred paths where applicable, while the additional paths through HQ-RTR02 provided alternate routing connectivity.

OSPF participation was limited to the routed interfaces required for neighbor formation across the final redundant topology.

---

## WAN Redundancy Implementation

Additional WAN connections were established between HQ-RTR02 and both Branch routers.

BR1-RTR01 and BR2-RTR01 therefore maintain routed WAN connectivity through both Headquarters edge routers.

The existing WAN connections through HQ-RTR01 remain the preferred paths during normal operation.

OSPF interface costs were applied to the additional HQ-RTR02 WAN paths so that they could provide alternate routing connectivity when a preferred WAN connection became unavailable.

---

## Internet Redundancy Implementation

A second external IPv4 connection was established between HQ-RTR02 and ISP-RTR01.

HQ-RTR02 was configured with its own external IPv4 connection and default route toward ISP-RTR01.

NAT/PAT was implemented on HQ-RTR02 for the existing internal enterprise IPv4 networks.

The existing Internet connection and NAT/PAT implementation on HQ-RTR01 were preserved.

This provides two Headquarters edge paths capable of supporting IPv4 Internet connectivity.

OSPF default-route advertisement was integrated with the redundant routing architecture to distribute external reachability through the enterprise routing domain.

---

## IPv6 Redundancy Implementation

IPv6 addressing was extended across the additional routed links introduced in Project 11.

New IPv6 transit networks were assigned to the redundant connections between:

- HQ-RTR01 and HQ-MLS02
- HQ-RTR02 and HQ-MLS01
- HQ-RTR02 and HQ-MLS02
- HQ-RTR02 and BR1-RTR01
- HQ-RTR02 and BR2-RTR01
- HQ-RTR02 and ISP-RTR01

The existing IPv6 addressing on the original enterprise links and LAN networks was preserved.

This extended the existing dual-stack architecture across the redundant topology without modifying the previously implemented IPv6 LAN addressing.

---

## OSPFv3 Redundancy Implementation

The existing OSPFv3 routing domain was extended across the additional IPv6 transit links.

HQ-RTR02 was added to the OSPFv3 topology using router ID `7.7.7.7`.

OSPFv3 was enabled on the additional Headquarters, WAN, and ISP routed connections required for IPv6 redundancy.

The additional IPv6 routing path between HQ-RTR01 and HQ-MLS02 was also integrated into the OSPFv3 topology.

OSPFv3 interface costs were applied to differentiate preferred and backup IPv6 routing paths.

OSPFv3 participation was limited to the routed interfaces required for neighbor formation across the final redundant IPv6 topology.

---

## Management Workstation Implementation

A dedicated Linux management workstation, `linux-mgmt01`, was added to the existing Management VLAN.

The workstation provides a centralized endpoint for administrative connectivity and SSH-based verification of enterprise network devices.

The final management configuration uses:

- IPv4 address: `192.168.99.10/24`
- Default gateway: `192.168.99.254`

The workstation uses the existing Management VLAN infrastructure and HSRP virtual gateway without modifying the Management VLAN architecture.

---

## Existing Services Integration

The enterprise services implemented throughout the previous projects were preserved as part of the final architecture.

These include:

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

Project 11 does not redesign these existing services.

The final implementation integrates them with the additional Layer 3, WAN, Internet, IPv4, and IPv6 routing infrastructure introduced in Project 11.

---

## Implementation Result

The final NorthStar Enterprise Network integrates the existing enterprise services with redundant Headquarters Layer 3 paths, Branch WAN connections, Internet connectivity, and IPv6 routing.

OSPFv2 and OSPFv3 provide dynamic routing across the redundant infrastructure, while the existing HSRP implementation continues to provide redundant IPv4 default gateways for the Headquarters VLANs.

The resulting architecture provides multiple routing paths while preserving the enterprise infrastructure developed throughout the previous projects.