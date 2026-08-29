
# Project 04 – WAN Connectivity & Static Routing

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item | Value |
|------|-------|
| Project | Project 04 – WAN Connectivity & Static Routing |
| Version | v4.0 |
| Status | Completed |
| Platform | EVE-NG |
| Vendor | Cisco |

---

## Overview

Project 04 extends the NorthStar Enterprise Network from a single-site campus into a multi-site enterprise by introducing Wide Area Network (WAN) connectivity between Headquarters and two branch offices.

The existing Headquarters infrastructure is retained while dedicated WAN routers and point-to-point WAN links are introduced to interconnect geographically separated locations. Static Routing provides end-to-end communication between Headquarters and both branch offices.

---

## Objectives

- Extend the enterprise network to multiple sites.
- Deploy a hub-and-spoke WAN topology.
- Configure point-to-point WAN links.
- Integrate the Headquarters campus with the WAN edge router.
- Implement Static Routing between Headquarters and the branch offices.
- Verify end-to-end WAN connectivity.

---

## Technologies Used

- Cisco IOS
- Cisco IOL (L2/L3)
- Static Routing
- IPv4 Routing
- Point-to-Point WAN Links
- Hub-and-Spoke Topology
- Layer 3 Routing
- ICMP
- EVE-NG
- Cisco IOS CLI

---

## Project Structure

```text
Project-04-WAN-Connectivity-Static-Routing/
│
├── 01-Requirements
├── 02-Network-Design-Specification
├── 03-Implementation
├── 04-Verification
├── 05-Troubleshooting
├── 06-Lessons-Learned
├── Assets
├── Configurations
│   └── 1. Configuration-Scope
│   ├── BR1-RTR01
│   ├── BR1-SW01
│   ├── BR2-RTR01
│   ├── HQ-MLS01
│   └── HQ-RTR01
├── Screenshots
└── README
```

---

## Enterprise Network Topology

![Figure 1. Enterprise WAN Connectivity & Static Routing](Assets/Figure%201.%20Enterprise%20WAN%20Connectivity%20&%20Static%20Routing.png)

The existing Headquarters campus infrastructure is retained from Project 03.

Project 04 introduces HQ-RTR01 as the Headquarters WAN edge router together with one router and one access switch at each branch office.

The resulting hub-and-spoke WAN topology enables communication between Headquarters, Branch 1, and Branch 2 using Static Routing.

---

## IPv4 Addressing

### WAN and Headquarters Transit Networks

| Connection | Network | Endpoint Addresses |
|---|---|---|
| HQ-RTR01 ↔ BR1-RTR01 | 10.0.0.0/30 | 10.0.0.1 ↔ 10.0.0.2 |
| HQ-RTR01 ↔ BR2-RTR01 | 10.0.0.4/30 | 10.0.0.5 ↔ 10.0.0.6 |
| HQ-RTR01 ↔ HQ-MLS01 | 10.0.0.8/30 | 10.0.0.9 ↔ 10.0.0.10 |

### Branch LAN Networks

| Site | Network | Default Gateway |
|---|---|---|
| Branch 1 | 192.168.40.0/24 | 192.168.40.1 |
| Branch 2 | 192.168.50.0/24 | 192.168.50.1 |

The additional physical connection between HQ-RTR01 and HQ-MLS02 remains inactive and unaddressed during Project 04.

---

## Routing Design

HQ-MLS01 continues to provide Inter-VLAN Routing for the Headquarters networks, while HQ-RTR01 provides connectivity between the Headquarters campus and both branch offices.

Static Routes provide reachability between:

- Headquarters and Branch 1
- Headquarters and Branch 2
- Branch 1 and Branch 2

Traffic exchanged between the two branch offices is forwarded through HQ-RTR01.

---

## Verification Performed

The following items were successfully verified:

- Headquarters routing tables
- Branch routing tables
- Required WAN and transit interface status
- Branch-to-Branch connectivity
- Headquarters-to-Branch connectivity
- Static Route operation

Verification screenshots are available in the **Screenshots** directory.

---

## Skills Demonstrated

- Enterprise WAN Deployment
- Static Routing
- Hub-and-Spoke Network Design
- IPv4 Routing
- Point-to-Point Network Addressing
- Layer 3 Transit Connectivity
- Cisco IOS CLI
- Network Verification
- Network Troubleshooting

---

## Result

Project 04 successfully expanded the NorthStar Enterprise Network into a multi-site enterprise environment by connecting Headquarters with two remote branch offices through dedicated WAN links.

Static Routing provides communication between the Headquarters networks and both branch LANs while also enabling communication between the two branch offices through the Headquarters WAN edge router.

The completed implementation establishes the WAN and Static Routing foundation of the NorthStar Enterprise Network.

---

## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio