
# Project 03 – Inter-VLAN Routing

## Project Overview

Project 03 extends the Enterprise Layer 2 foundation established in Project 02 by introducing Layer 3 communication between departmental VLANs.

The existing physical topology, VLAN structure, trunk links, Management VLAN, Voice VLANs, and Rapid PVST+ configuration are retained. Inter-VLAN Routing is introduced on HQ-MLS01 using Switch Virtual Interfaces (SVIs).

---

## Project Objectives

The objectives of this project are to:

- Preserve the existing Project 02 topology and Layer 2 configuration.
- Enable Layer 3 routing on HQ-MLS01.
- Create SVIs for the HR, Finance, and IT Data VLANs.
- Assign a default gateway to each departmental Data VLAN.
- Configure static IPv4 addressing on all end-user PCs.
- Enable communication between devices in different departmental VLANs.
- Verify the routing table, SVI status, and end-to-end connectivity.
- Establish the Layer 3 campus foundation for subsequent projects.

---

## Existing Infrastructure

Project 02 serves as the baseline for this project.

The following infrastructure is retained:

- HQ-MLS01
- HQ-MLS02
- HQ-SW01
- HQ-SW02
- HQ-SW03
- Six end-user PCs
- Six Cisco IP Phones
- Data VLANs
- Voice VLANs
- Management VLAN 99
- Native VLAN 999
- IEEE 802.1Q trunks
- Redundant Layer 2 uplinks
- Rapid PVST+
- Primary and Secondary Root Bridge configuration

The existing Layer 2 architecture remains unchanged while Layer 3 functionality is introduced on HQ-MLS01.

---

## New Implementation

Project 03 introduces:

- Layer 3 switching on HQ-MLS01
- SVIs for VLANs 10, 20, and 30
- Default gateways for departmental Data VLANs
- Static IPv4 addressing for end-user PCs
- Inter-VLAN communication

---

## Routing Requirements

- Enable Layer 3 routing on HQ-MLS01.
- Configure one SVI for each departmental Data VLAN.
- Provide a default gateway for each departmental Data VLAN.
- Configure static IPv4 addressing on all end-user PCs.
- Verify Inter-VLAN communication.

---

## Connectivity Requirements

The completed network must demonstrate:

- Successful communication within each departmental VLAN.
- Successful communication between different departmental VLANs.
- Successful communication from end-user PCs to their default gateways.
- Continued Management VLAN connectivity.
- Unchanged Layer 2 trunk and STP operation.

---

## Technical Constraints

This project is limited to Inter-VLAN Routing.

The following technologies are intentionally excluded:

- DHCP
- WAN connectivity
- Static routing between routers
- OSPF
- NAT
- ACL
- EtherChannel
- HSRP
- IPv6
- Advanced network security

Voice VLANs remain part of the Layer 2 design, but voice services and Voice VLAN routing are outside the scope of this project.

---

## Platform and Technologies

| Component | Technology |
| --- | --- |
| Lab Platform | EVE-NG |
| Network Devices | Cisco IOL |
| Layer 3 Switching | Multilayer Switch |
| Inter-VLAN Routing | Switch Virtual Interfaces |
| IP Addressing | Static IPv4 |
| Layer 2 Transport | IEEE 802.1Q |
| Documentation | Markdown |
| Network Diagram | draw.io |

---

## Project Deliverables

The completed project must include:

- Updated Requirements documentation
- Updated Network Design Specification
- Implementation documentation
- Verification documentation
- Troubleshooting documentation
- Lessons Learned
- Project 03 configuration additions
- Verification screenshots using the SC-xx naming convention
- Updated README

---

## Success Criteria

Project 03 is considered complete when:

- IPv4 routing is enabled on HQ-MLS01.
- SVIs for VLANs 10, 20, and 30 are operational.
- All PCs use the correct static IPv4 address and default gateway.
- Connected departmental VLAN networks appear in the routing table.
- Same-VLAN and Inter-VLAN communication are successful.
- Existing Project 02 Layer 2 services remain operational.
- Project documentation and verification evidence are complete.