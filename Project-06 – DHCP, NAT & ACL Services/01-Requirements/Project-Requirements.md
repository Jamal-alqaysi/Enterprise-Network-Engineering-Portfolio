
## Project Objective

Extend the NorthStar Enterprise Network by introducing centralized network services, including Dynamic Host Configuration Protocol (DHCP), Network Address Translation with Port Address Translation (NAT/PAT), and Access Control Lists (ACLs).

The existing enterprise topology and OSPF routing infrastructure are retained while centralized services are deployed at Headquarters and external connectivity is provided through ISP-RTR01.

---

## Functional Requirements

The implementation shall meet the following requirements:

- Preserve the existing enterprise topology implemented in Project 05.
- Maintain OSPF as the enterprise dynamic routing protocol.
- Deploy a centralized DHCP server at Headquarters.
- Configure DHCP Relay on branch routers to forward DHCP requests to Headquarters.
- Automatically assign IPv4 addresses to enterprise end devices.
- Configure NAT/PAT to provide access to the simulated Internet through ISP-RTR01.
- Configure Extended ACLs to enforce the enterprise security policy.
- Protect the Management VLAN from unauthorized branch access.
- Prevent direct communication between Branch 1 and Branch 2.
- Prevent ICMP Echo Requests from branch networks to the ISP router interface.
- Allow branch users to access authorized Headquarters networks.
- Allow branch users to access the simulated Internet resource.
- Verify successful DHCP address allocation across all enterprise sites.
- Verify successful NAT/PAT operation.
- Verify successful Internet connectivity.
- Verify ACL operation according to the defined enterprise security policy.

---

## Technical Requirements

### Platform

- EVE-NG Community Edition

### Network Devices

- HQ-MLS01
- HQ-RTR01
- BR1-RTR01
- BR2-RTR01
- BR1-SW01
- BR2-SW01
- ISP-RTR01

### Network Services

- Centralized DHCP Server
- DHCP Relay
- NAT/PAT
- Extended ACL
- Simulated Internet Connectivity

### Routing Protocol

- OSPFv2
- Area 0

### IP Version

- IPv4

---

## Expected Outcome

Upon completion of this project:

- OSPF continues to provide dynamic routing across the enterprise.
- End devices automatically receive IPv4 addresses from the centralized DHCP server.
- Branch offices obtain DHCP leases through DHCP Relay.
- NAT/PAT provides Internet access through ISP-RTR01.
- Branch users can reach the simulated Internet resource.
- Branch users cannot send ICMP Echo Requests directly to the ISP router interface.
- Branch users cannot access the Management VLAN.
- Direct communication between Branch 1 and Branch 2 is prevented.
- Authorized enterprise communication remains operational according to the defined security policy.