
## Overview

Project 06 builds directly on the dynamic routing infrastructure implemented in Project 05.

The existing enterprise IPv4 addressing plan, VLAN architecture, and OSPF routing environment are retained. This project introduces centralized DHCP services, DHCP Relay, Network Address Translation with Port Address Translation (NAT/PAT), Access Control Lists (ACLs), and simulated Internet connectivity through ISP-RTR01.

Headquarters continues to function as the central enterprise site, providing centralized network services and external connectivity to both branch offices.

---

## Network Topology

The enterprise topology from Project 05 is extended by introducing ISP-RTR01.

ISP-RTR01 is connected directly to HQ-RTR01 and represents the external network. A loopback interface on ISP-RTR01 provides a simulated Internet resource for external connectivity testing.

No additional Internet workstation or Internet cloud is required.

![Figure 1. Enterprise Network Services Topology](../Assets/Figure%201.%20Enterprise%20Network%20Services%20Topology.png)

---

## Enterprise Services Design

Centralized network services are distributed across the appropriate Layer 3 devices.

| Service | Device |
|---------|---------|
| DHCP Server | HQ-MLS01 |
| DHCP Relay | BR1-RTR01, BR2-RTR01 |
| NAT/PAT | HQ-RTR01 |
| Branch Security ACLs | BR1-RTR01, BR2-RTR01 |
| Internet Simulation | ISP-RTR01 |
| Dynamic Routing | OSPF Area 0 |

---

## DHCP Design

A centralized DHCP service is hosted on HQ-MLS01.

DHCP pools provide dynamic IPv4 addressing for the Headquarters departmental VLANs and both branch LANs.

Headquarters clients communicate directly with the DHCP service through their local SVIs. DHCP Relay is configured on the branch router LAN interfaces to forward DHCP requests from remote clients to HQ-MLS01.

The existing default gateway addresses remain unchanged.

### DHCP Networks

| Site | Network | Default Gateway |
|------|---------|-----------------|
| HR | 192.168.10.0/24 | 192.168.10.1 |
| Finance | 192.168.20.0/24 | 192.168.20.1 |
| IT | 192.168.30.0/24 | 192.168.30.1 |
| Branch 1 | 192.168.40.0/24 | 192.168.40.1 |
| Branch 2 | 192.168.50.0/24 | 192.168.50.1 |

### DHCP Address Allocation

The first twenty addresses in each DHCP network are excluded from dynamic allocation.

| Network | Excluded Range |
|---------|----------------|
| 192.168.10.0/24 | 192.168.10.1 – 192.168.10.20 |
| 192.168.20.0/24 | 192.168.20.1 – 192.168.20.20 |
| 192.168.30.0/24 | 192.168.30.1 – 192.168.30.20 |
| 192.168.40.0/24 | 192.168.40.1 – 192.168.40.20 |
| 192.168.50.0/24 | 192.168.50.1 – 192.168.50.20 |

All DHCP pools use `8.8.8.8` as the configured DNS server.

---

## DHCP Relay Design

The branch LANs are separated from the centralized DHCP server by Layer 3 routing.

DHCP Relay is therefore configured on the LAN-facing interfaces of BR1-RTR01 and BR2-RTR01.

Both branch routers forward DHCP requests to the centralized DHCP service on HQ-MLS01 using:

`10.0.0.10`

This allows branch clients to obtain IPv4 addressing from the centralized DHCP server without requiring a local DHCP service at each branch.

---

## Internet Connectivity Design

HQ-RTR01 is connected directly to ISP-RTR01 through a dedicated public point-to-point network.

### Public WAN Connection

| Connection | Network | HQ-RTR01 | ISP-RTR01 |
|------------|---------|----------|-----------|
| HQ-RTR01 ↔ ISP-RTR01 | 203.0.113.0/30 | 203.0.113.1 | 203.0.113.2 |

ISP-RTR01 represents the external network. A loopback interface is configured on the ISP router to simulate an Internet resource without introducing another physical device.

### Simulated Internet Resource

| Device | Interface | IP Address | Purpose |
|--------|-----------|------------|---------|
| ISP-RTR01 | Loopback0 | 203.0.114.10/32 | Simulated Internet Resource |

The loopback address provides a separate external destination for testing Internet access through NAT/PAT.

---

## NAT/PAT Design

NAT/PAT is implemented on HQ-RTR01.

Enterprise-facing interfaces are classified as NAT inside interfaces, while the interface connected to ISP-RTR01 is classified as the NAT outside interface.

The following internal networks are eligible for translation:

- `192.168.10.0/24`
- `192.168.20.0/24`
- `192.168.30.0/24`
- `192.168.40.0/24`
- `192.168.50.0/24`

These internal networks share the IPv4 address assigned to the ISP-facing interface of HQ-RTR01 when accessing external destinations.

A dedicated standard ACL named `NAT_INSIDE` identifies the internal networks eligible for address translation. This ACL is used only for NAT classification and is separate from the Extended ACLs applied at the branch offices.

---

## ACL Design

Extended ACLs are applied inbound on the branch router LAN interfaces, placing traffic controls close to the source.

The security policy permits DHCP operation, authorized Headquarters access, and external connectivity while protecting the Management VLAN and maintaining separation between the two branch offices.

### DHCP and ACL Interaction

Branch clients initially send DHCP requests before they have been assigned an IPv4 address.

The initial DHCP exchange uses UDP traffic between the DHCP client and server ports. Because the branch security ACLs are applied inbound on the LAN-facing interfaces, DHCP traffic must be explicitly permitted before the remaining branch security policy is evaluated.

The branch ACLs therefore permit DHCP client and server traffic before applying the enterprise access restrictions.

### Branch Security Policy

| Traffic | Action |
|---------|--------|
| DHCP client/server traffic | Permit |
| Branch LAN → Management VLAN 99 | Deny |
| Branch 1 LAN → Branch 2 LAN | Deny |
| Branch 2 LAN → Branch 1 LAN | Deny |
| Branch LAN → ISP interface using ICMP Echo | Deny |
| Branch LAN → HQ VLAN 10 | Permit |
| Branch LAN → HQ VLAN 20 | Permit |
| Branch LAN → HQ VLAN 30 | Permit |
| Branch LAN → Other destinations | Permit |

The DHCP permit entries ensure that branch clients can obtain their IPv4 configuration from the centralized DHCP service before the remaining ACL policy is evaluated.

The policy prevents branch users from sending ICMP Echo Requests directly to the ISP router interface at `203.0.113.2`.

This restriction does not prevent access to the simulated Internet resource at `203.0.114.10`.

### ACL Placement

| Device | Interface | Direction | ACL |
|--------|-----------|-----------|-----|
| BR1-RTR01 | Ethernet0/1 | Inbound | BR1-LAN-POLICY |
| BR2-RTR01 | Ethernet0/1 | Inbound | BR2-LAN-POLICY |

---

## Routing Design

The OSPF routing infrastructure implemented in Project 05 remains operational throughout the enterprise.

HQ-MLS01, HQ-RTR01, BR1-RTR01, and BR2-RTR01 continue to exchange internal enterprise routes dynamically through OSPF Area 0.

ISP-RTR01 does not participate in the internal OSPF routing domain.

HQ-RTR01 uses a default route toward ISP-RTR01 for external destinations. The default route is advertised into OSPF so that the Headquarters campus and both branches can forward external traffic toward HQ-RTR01.

The existing internal enterprise networks are not advertised to ISP-RTR01.

---

## Verification Design

The implementation is verified by confirming:

- Dynamic DHCP allocation at Headquarters.
- DHCP Relay operation at both branches.
- Successful DHCP operation through the branch security ACLs.
- Continued OSPF operation.
- Default-route propagation across the enterprise.
- NAT/PAT translations on HQ-RTR01.
- Successful access to `203.0.114.10`.
- Failed ICMP Echo Requests from branch clients to `203.0.113.2`.
- Failed access from branch LANs to Management VLAN 99.
- Failed direct communication between Branch 1 and Branch 2.
- Continued access from branch clients to authorized Headquarters networks.

---

## Design Summary

Project 06 introduces centralized DHCP services, DHCP Relay, NAT/PAT, Extended ACLs, and simulated Internet connectivity while preserving the existing OSPF routing architecture.

HQ-MLS01 provides centralized DHCP services, the branch routers provide DHCP Relay and source-based traffic filtering, and HQ-RTR01 provides NAT/PAT and external connectivity through ISP-RTR01.

ISP-RTR01 represents the external network, while its Loopback0 interface provides the simulated Internet resource used for connectivity testing.

The branch ACL design explicitly permits the DHCP traffic required for centralized address allocation before enforcing the remaining security policy.

The ACL policy protects the Management VLAN, isolates the branch LANs, prevents direct ICMP Echo Requests to the ISP infrastructure interface, and continues to permit authorized Headquarters and external access.