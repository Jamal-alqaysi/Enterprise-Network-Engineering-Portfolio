
# Project 06 – DHCP, NAT & ACL Services

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item | Value |
|------|-------|
| Project | Project 06 – DHCP, NAT & ACL Services |
| Version | v6.0 |
| Status | Completed |
| Platform | EVE-NG |
| Vendor | Cisco |

---

## Overview

Project 06 extends the NorthStar Enterprise Network by introducing centralized DHCP services, DHCP Relay, Network Address Translation using Port Address Translation (NAT/PAT), Access Control Lists (ACLs), and simulated Internet connectivity.

The existing IPv4 addressing plan, VLAN architecture, and OSPF routing infrastructure are retained while centralized enterprise services and external connectivity are introduced.

ISP-RTR01 is added to represent the external network, while a loopback interface provides a simulated Internet resource for connectivity testing.

---

## Objectives

- Preserve the existing OSPF-based enterprise routing infrastructure.
- Deploy centralized DHCP services at Headquarters.
- Provide dynamic IPv4 addressing to Headquarters and branch clients.
- Implement DHCP Relay at both branch offices.
- Introduce simulated Internet connectivity through ISP-RTR01.
- Implement NAT/PAT on the Headquarters edge router.
- Advertise a default route through the existing OSPF domain.
- Implement Extended ACLs at the branch offices.
- Protect the Management VLAN from unauthorized branch access.
- Prevent direct communication between Branch 1 and Branch 2.
- Restrict direct ICMP Echo Requests from branch clients to the ISP infrastructure interface.
- Maintain authorized access to Headquarters networks and the simulated Internet resource.
- Verify successful operation of all introduced services and security policies.

---

## Technologies Used

- Cisco IOS
- Cisco IOL
- IPv4
- DHCP
- DHCP Relay
- NAT/PAT
- Extended Access Control Lists
- OSPFv2
- OSPF Default Route Advertisement
- Static Default Routing
- EVE-NG
- Cisco IOS CLI

---

## Project Structure

```text
Project-06-DHCP-NAT-ACL-Services/
│
├── 01-Requirements
├── 02-Network-Design-Specification
├── 03-Implementation
├── 04-Verification
├── 05-Troubleshooting
├── 06-Lessons-Learned
├── Assets
├── Configurations
│   ├── 1.Configuration-Scope
│   ├── HQ-RTR01
│   ├── BR1-RTR01
│   ├── BR2-RTR01
│   ├── ISP-RTR01
│   └── HQ-MLS01
├── Screenshots
└── README
```

---

## Enterprise Network Topology

![Figure 1. Enterprise Network Services Topology](Assets/Figure%201.%20Enterprise%20Network%20Services%20Topology.png)

Project 06 extends the existing enterprise topology by introducing ISP-RTR01.

ISP-RTR01 is directly connected to HQ-RTR01 and represents the external network. Its Loopback0 interface provides the simulated Internet resource used for external connectivity verification.

---

## Enterprise Services

| Service | Device |
|---------|---------|
| Centralized DHCP Server | HQ-MLS01 |
| DHCP Relay | BR1-RTR01, BR2-RTR01 |
| NAT/PAT | HQ-RTR01 |
| Branch Security ACLs | BR1-RTR01, BR2-RTR01 |
| Internet Simulation | ISP-RTR01 |
| Dynamic Routing | OSPF Area 0 |

---

## DHCP Design

HQ-MLS01 provides centralized DHCP services for the Headquarters departmental VLANs and both branch LANs.

| Site | Network | Default Gateway |
|------|---------|-----------------|
| HR | 192.168.10.0/24 | 192.168.10.1 |
| Finance | 192.168.20.0/24 | 192.168.20.1 |
| IT | 192.168.30.0/24 | 192.168.30.1 |
| Branch 1 | 192.168.40.0/24 | 192.168.40.1 |
| Branch 2 | 192.168.50.0/24 | 192.168.50.1 |

The first twenty addresses in each DHCP network are excluded from dynamic allocation.

Branch clients use DHCP Relay on BR1-RTR01 and BR2-RTR01 to reach the centralized DHCP service at Headquarters.

---

## Internet Connectivity

HQ-RTR01 connects the enterprise network to ISP-RTR01 through the following public IPv4 network:

| Connection | Network | HQ-RTR01 | ISP-RTR01 |
|------------|---------|----------|-----------|
| HQ-RTR01 ↔ ISP-RTR01 | 203.0.113.0/30 | 203.0.113.1 | 203.0.113.2 |

ISP-RTR01 uses the following loopback interface as the simulated Internet resource:

| Interface | IP Address | Purpose |
|-----------|------------|---------|
| Loopback0 | 203.0.114.10/32 | Simulated Internet Resource |

---

## NAT/PAT

NAT/PAT is implemented on HQ-RTR01.

The enterprise-facing routed interfaces are classified as NAT inside interfaces, while the interface connected to ISP-RTR01 is classified as NAT outside.

A dedicated NAT classification ACL identifies the internal enterprise networks eligible for translation.

PAT allows multiple internal enterprise clients to share the public IPv4 address assigned to the ISP-facing interface of HQ-RTR01.

---

## Default Routing

HQ-RTR01 uses a static default route toward ISP-RTR01 for external destinations.

The default route is advertised into the existing OSPF Area 0 routing domain, allowing Headquarters and both branch offices to forward external traffic toward HQ-RTR01.

ISP-RTR01 does not participate in the internal OSPFv2 routing domain.

---

## ACL Security Policy

Extended ACLs are applied inbound on the LAN-facing interfaces of BR1-RTR01 and BR2-RTR01.

The branch security policy:

- Permits the DHCP traffic required for centralized address allocation.
- Denies branch access to Management VLAN 99.
- Prevents direct communication between Branch 1 and Branch 2.
- Denies ICMP Echo Requests from branch clients to the ISP router interface.
- Permits access to authorized Headquarters departmental networks.
- Permits access to the simulated Internet resource and other authorized external destinations.

The DHCP permit entries are evaluated before the remaining branch security policy so that clients can obtain IPv4 addresses through DHCP Relay while the ACLs remain active.

---

## Verification Performed

The following items were successfully verified:

- EVE-NG lab deployment
- OSPF default route propagation
- DHCP pool operation
- DHCP bindings
- DHCP Relay
- NAT/PAT translations
- NAT statistics
- Headquarters access from branch networks
- Branch ACL security policy
- Simulated Internet connectivity
- ACL hit counters

Verification evidence is available in the **Screenshots** directory.

---

## Troubleshooting

Troubleshooting performed during Project 06 included:

- OSPF default route advertisement
- NAT/PAT inside and outside interface configuration
- Branch ACL application
- DHCP Relay configuration
- DHCP operation through the inbound branch ACLs

During DHCP troubleshooting, the branch security ACL was identified as preventing the initial DHCP client traffic from reaching the DHCP Relay process.

The ACL policy was updated to permit the required DHCP traffic before the remaining security rules, allowing branch clients to receive addresses from the centralized DHCP server while preserving the branch security policy.

---

## Skills Demonstrated

- Centralized DHCP Deployment
- DHCP Relay
- DHCP Troubleshooting
- NAT/PAT
- NAT Inside and Outside Interface Classification
- Extended ACL Configuration
- ACL Placement and Rule Ordering
- OSPF Default Route Advertisement
- Static Default Routing
- IPv4 Routing
- Enterprise Edge Connectivity
- Network Security Policy Implementation
- Cisco IOS CLI
- EVE-NG Network Simulation
- Network Verification
- Technical Troubleshooting
- Technical Documentation

---

## Result

Project 06 successfully integrated centralized network services and external connectivity into the existing NorthStar Enterprise Network.

HQ-MLS01 provides centralized DHCP services, BR1-RTR01 and BR2-RTR01 provide DHCP Relay and branch traffic filtering, HQ-RTR01 provides NAT/PAT and external routing, and ISP-RTR01 provides the simulated external network environment.

DHCP allocation, DHCP Relay, NAT/PAT, OSPF default route propagation, Internet connectivity, and branch ACL policies were successfully verified while preserving the existing OSPF-based enterprise routing infrastructure.

---

## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio