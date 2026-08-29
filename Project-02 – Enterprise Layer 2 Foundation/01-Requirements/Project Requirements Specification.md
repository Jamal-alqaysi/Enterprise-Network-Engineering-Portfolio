

# Project 02 – Enterprise Layer 2 Foundation

## Overview

Project 02 builds directly on the infrastructure established in Project 01 by introducing the enterprise Layer 2 architecture of the NorthStar Enterprise Network.

The project expands the Headquarters infrastructure with a second multilayer switch and six Cisco IP Phones. Departmental Data VLANs, dedicated Voice VLANs, a Management VLAN, a Native VLAN, IEEE 802.1Q trunking, redundant Layer 2 connectivity, and Rapid PVST+ are introduced to create a structured and scalable switching environment.

The existing enterprise workstations and access switches from Project 01 are retained while the network is logically segmented according to departmental and traffic requirements.

---

## Objectives

- Integrate HQ-MLS02 into the Headquarters switching infrastructure.
- Add six Cisco IP Phones across the enterprise access layer.
- Configure departmental Data VLANs.
- Configure dedicated Voice VLANs for the Cisco IP Phones.
- Configure a dedicated Management VLAN.
- Configure VLAN 999 as the Native VLAN.
- Configure IEEE 802.1Q trunk links between enterprise switches.
- Configure access interfaces for Data and Voice VLANs.
- Introduce redundant Layer 2 connectivity.
- Enable Rapid PVST+ to prevent Layer 2 switching loops.
- Configure deterministic STP root bridge selection.
- Verify VLAN segmentation, trunk operation, and Layer 2 connectivity.
- Establish the Layer 2 foundation for subsequent NorthStar projects.

---

## Existing Infrastructure

Project 01 provides the baseline infrastructure for Project 02.

The following devices are retained:

- HQ-MLS01
- HQ-SW01
- HQ-SW02
- HQ-SW03
- HR-PC01
- HR-PC02
- FIN-PC01
- FIN-PC02
- IT-PC01
- IT-PC02

The device naming convention, initial management configuration, and documentation standards established in Project 01 are preserved.

---

## New Infrastructure

Project 02 introduces:

- HQ-MLS02 as a second Headquarters multilayer switch.
- HR-IPPhone01
- HR-IPPhone02
- FIN-IPPhone01
- FIN-IPPhone02
- IT-IPPhone01
- IT-IPPhone02
- Departmental Data VLANs.
- Departmental Voice VLANs.
- A dedicated Management VLAN.
- A dedicated Native VLAN.
- IEEE 802.1Q trunk links.
- Redundant Layer 2 paths.
- Rapid PVST+.

---

## VLAN Requirements

The following VLANs are introduced:

| VLAN ID | VLAN Name | Purpose |
| --- | --- | --- |
| 10 | HR | Human Resources Data |
| 20 | FINANCE | Finance Data |
| 30 | IT | Information Technology Data |
| 99 | MANAGEMENT | Network Device Management |
| 110 | HR-VOICE | Human Resources Voice |
| 120 | FINANCE-VOICE | Finance Voice |
| 130 | IT-VOICE | Information Technology Voice |
| 999 | NATIVE | Native VLAN for trunk links |

Data and Voice traffic must remain logically separated while sharing the same physical access infrastructure.

VLAN 1 is not used for enterprise user or management traffic.

---

## Management Addressing Requirements

Network device management is migrated from the Project 01 `192.168.0.0/24` network to the dedicated Management VLAN 99.

| Device | Management IPv4 Address |
| --- | --- |
| HQ-MLS01 | 192.168.99.1/24 |
| HQ-MLS02 | 192.168.99.2/24 |
| HQ-SW01 | 192.168.99.11/24 |
| HQ-SW02 | 192.168.99.12/24 |
| HQ-SW03 | 192.168.99.13/24 |

The access switches use `192.168.99.1` as their management default gateway.

---

## Endpoint Distribution

The Project 01 enterprise workstations are retained, while six Cisco IP Phones are added to the access layer.

The approved endpoint distribution is:

| Access Switch | Connected Endpoints |
| --- | --- |
| HQ-SW01 | HR-PC01, HR-IPPhone01, FIN-PC01, FIN-IPPhone01 |
| HQ-SW02 | IT-PC01, IT-IPPhone01, HR-PC02, HR-IPPhone02 |
| HQ-SW03 | FIN-PC02, FIN-IPPhone02, IT-PC02, IT-IPPhone02 |

The endpoint distribution demonstrates how departmental Data and Voice VLANs can extend across multiple access switches through the enterprise trunk infrastructure.

---

## Trunking Requirements

- Switch-to-switch links must operate as IEEE 802.1Q trunks.
- Required Data, Voice, and Management VLANs must be transported across the trunk infrastructure.
- VLAN 999 must be configured as the Native VLAN.
- The allowed VLAN list must be explicitly defined.
- Trunk configuration must remain consistent between connected interfaces.
- VLAN 1 must not be used for enterprise user or management traffic.

---

## Spanning Tree Requirements

The redundant Layer 2 topology requires a loop-prevention mechanism.

Rapid PVST+ must be enabled across the enterprise switching infrastructure.

The design must satisfy the following requirements:

- Rapid PVST+ must operate across the Layer 2 topology.
- HQ-MLS01 must operate as the preferred STP root bridge.
- HQ-MLS02 must operate as the secondary STP root bridge.
- Root bridge selection must be deterministic.
- Redundant Layer 2 paths must transition to the appropriate STP state to prevent switching loops.
- STP operation must be verified before the project is considered complete.

EtherChannel is intentionally excluded from Project 02 and is introduced in a later project.

---

## Connectivity Requirements

The completed Layer 2 infrastructure must demonstrate:

- Successful same-VLAN communication across different access switches.
- Isolation between different Data VLANs.
- Successful IEEE 802.1Q trunk operation.
- Correct Data VLAN assignment.
- Correct Voice VLAN assignment.
- Successful Management VLAN connectivity.
- Stable Rapid PVST+ operation.

Inter-VLAN communication is not required in Project 02 because Layer 3 routing between VLANs has not yet been introduced.

---

## Project Scope

### Included

- HQ-MLS02 integration
- Cisco IP Phone deployment
- Data VLANs
- Voice VLANs
- Management VLAN
- Native VLAN
- IEEE 802.1Q Trunking
- Data and Voice access port configuration
- Redundant Layer 2 connectivity
- Rapid PVST+
- STP root bridge selection
- Layer 2 connectivity verification

### Excluded

The following technologies are intentionally excluded from Project 02:

- Inter-VLAN Routing
- Static Routing
- OSPF
- DHCP
- NAT/PAT
- ACLs
- EtherChannel
- HSRP
- IPv6
- Advanced Layer 2 Security
- IP Telephony Services

The Cisco IP Phones are introduced to demonstrate Voice VLAN segmentation. Call processing and IP telephony services are outside the scope of this project.

---

## Expected Outcome

Upon completion, the NorthStar Enterprise Network will provide a segmented and redundant Layer 2 infrastructure supporting departmental Data VLANs, dedicated Voice VLANs, network management, IEEE 802.1Q trunking, and Rapid PVST+.

The existing enterprise workstations and newly introduced Cisco IP Phones will be logically separated into their appropriate Data and Voice VLANs while maintaining stable Layer 2 connectivity across the Headquarters infrastructure.

The completed architecture establishes the Layer 2 foundation required for the Layer 3 technologies and enterprise services introduced in subsequent NorthStar projects.