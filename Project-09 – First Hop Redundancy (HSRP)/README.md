
# Project 09 – First Hop Redundancy (HSRP)

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)

![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item | Value |
|------|-------|
| Project | Project 09 – First Hop Redundancy (HSRP) |
| Version | v9.0 |
| Status | Completed |
| Platform | EVE-NG |
| Vendor | Cisco |

---

## Overview

Project 09 builds directly on the enterprise infrastructure implemented in Project 08 by introducing first-hop gateway redundancy using the Hot Standby Router Protocol (HSRP).

The existing enterprise topology, Dual Stack architecture, VLAN design, Layer 2 redundancy, OSPF, NAT, ACL, and other previously implemented enterprise services are preserved. HSRP is deployed across the Headquarters multilayer switches to provide redundant default gateway operation for the Headquarters VLANs, while the Headquarters DHCP configuration is updated to distribute the HSRP virtual gateway addresses.

---

## Objectives

- Deploy HSRP across the Headquarters multilayer switches.
- Provide default gateway redundancy for all Headquarters VLANs.
- Configure Active and Standby gateway operation.
- Implement automatic gateway failover and recovery.
- Update DHCP to distribute the HSRP virtual gateway addresses.
- Maintain compatibility with enterprise services implemented in previous projects.

---

## Technologies Used

- Cisco IOS
- Cisco IOL (L2/L3)
- HSRP Version 2
- IPv4
- IPv6
- Dual Stack
- OSPFv2
- OSPFv3
- DHCP
- DHCP Relay
- NAT/PAT
- ACL
- EtherChannel
- Rapid PVST+
- EVE-NG
- CLI Configuration

---

## Project Structure

```text
Project-09-First-Hop-Redundancy-HSRP/
│
├── 01-Requirements
├── 02-Network-Design-Specification
├── 03-Implementation
├── 04-Verification
├── 05-Troubleshooting
├── 06-Lessons-Learned
├── Assets
├── Configurations
│   ├── 1. Configuration-Scope
│   ├── HQ-MLS01
│   └── HQ-MLS02
├── Screenshots
└── README
```

---

## Enterprise Network Topology

![Figure 1. Enterprise First Hop Redundance (HSRP) Topology](Assets/Figure%201.%20Enterprise%20First%20Hop%20Redundance%20(HSRP)%20Topology.png)

The physical topology remains unchanged from Project 08.

Gateway redundancy is introduced by deploying HSRP on the Headquarters multilayer switches while preserving the existing enterprise infrastructure and previously implemented services.

---

## Verification Performed

The following items were successfully verified:

- HQ-MLS01 HSRP Active operation
- HQ-MLS02 HSRP Standby operation
- HSRP virtual gateway configuration
- DHCP virtual gateway assignment
- End-to-end enterprise connectivity
- Branch-to-Headquarters connectivity
- VLAN 10 HSRP failover and failback
- Enterprise topology validation

Verification screenshots are available in the **Screenshots** directory.

---

## Skills Demonstrated

- HSRP Configuration
- Gateway Redundancy
- First Hop Redundancy Protocol (FHRP)
- High Availability
- DHCP Integration
- HSRP Failover and Recovery
- Enterprise Network Verification
- Network Troubleshooting
- Cisco IOS CLI

---

## Result

Project 09 successfully integrated HSRP into the NorthStar Enterprise Network, providing redundant default gateway operation for the Headquarters VLANs.

HQ-MLS01 operates as the preferred Active gateway and HQ-MLS02 as the Standby gateway. Headquarters clients use the HSRP virtual IP addresses as their default gateways, and the DHCP configuration distributes the corresponding virtual gateway addresses.

HSRP failover and failback were successfully validated for VLAN 10, confirming the expected gateway role transition and recovery behavior while preserving the same virtual default gateway address.

The resulting first-hop redundancy architecture provides a more resilient foundation for the Enterprise Security technologies introduced in Project 10.

---

## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio