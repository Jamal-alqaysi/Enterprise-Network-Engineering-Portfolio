
# Project 03 – Inter-VLAN Routing

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item | Value |
| --- | --- |
| Project | Project 03 – Inter-VLAN Routing |
| Version | v3.0 |
| Status | Completed |
| Platform | EVE-NG |
| Vendor | Cisco |

---

## Overview

Project 03 builds directly on the Enterprise Layer 2 foundation established in Project 02 by introducing Inter-VLAN Routing.

The existing physical topology and Layer 2 infrastructure are retained. Layer 3 communication between the HR, Finance, and IT Data VLANs is introduced on HQ-MLS01 using Switch Virtual Interfaces (SVIs).

---

## Objectives

- Preserve the existing Project 02 Layer 2 infrastructure.
- Enable Layer 3 routing on HQ-MLS01.
- Configure SVIs for the departmental Data VLANs.
- Provide IPv4 default gateways for the HR, Finance, and IT VLANs.
- Configure static IPv4 addressing on the enterprise workstations.
- Enable communication between departmental VLANs.
- Verify SVI status, connected routes, and Inter-VLAN connectivity.

---

## Technologies Used

- Cisco IOS
- Cisco IOL
- Multilayer Switching
- Inter-VLAN Routing
- Switch Virtual Interfaces (SVIs)
- IPv4
- Static IPv4 Addressing
- VLANs
- IEEE 802.1Q Trunking
- Rapid PVST+
- EVE-NG
- Cisco IOS CLI
- Draw.io
- Markdown

---

## Project Structure

```text
Project-03-Inter-VLAN-Routing/
│
├── 01-Requirements
├── 02-Network-Design-Specification
├── 03-Implementation
├── 04-Verification
├── 05-Troubleshooting
├── 06-Lessons-Learned
├── Assets
├── Configurations
│   └── 1.Configuration-Scope
│   └── HQ-MLS01
├── Screenshots
└── README
```

---

## Enterprise Network Topology

![Figure 3. Enterprise Inter-VLAN Routing Topology](Assets/Figure%203.%20Enterprise%20Inter-VLAN%20Routing%20Topology.png)

The physical enterprise topology remains unchanged from Project 02.

HQ-MLS01 provides Layer 3 communication between the HR, Finance, and IT Data VLANs through dedicated SVIs, while HQ-MLS02 continues to operate within the existing Layer 2 infrastructure.

No additional network devices or physical connections are introduced in Project 03.

---

## IPv4 Addressing

| VLAN | Department | Network         | Default Gateway |
| :--- | ---------- | --------------- | --------------- |
| 10   | HR         | 192.168.10.0/24 | 192.168.10.1    |
| 20   | FINANCE    | 192.168.20.0/24 | 192.168.20.1    |
| 30   | IT         | 192.168.30.0/24 | 192.168.30.1    |
| 99   | MANAGEMENT | 192.168.99.0/24 | 192.168.99.1    |

### End-Device Addressing

| Device | VLAN | IPv4 Address | Default Gateway |
| --- | ---: | --- | --- |
| HR-PC01 | 10 | 192.168.10.11/24 | 192.168.10.1 |
| HR-PC02 | 10 | 192.168.10.12/24 | 192.168.10.1 |
| FIN-PC01 | 20 | 192.168.20.11/24 | 192.168.20.1 |
| FIN-PC02 | 20 | 192.168.20.12/24 | 192.168.20.1 |
| IT-PC01 | 30 | 192.168.30.11/24 | 192.168.30.1 |
| IT-PC02 | 30 | 192.168.30.12/24 | 192.168.30.1 |

Static IPv4 addressing is used for the enterprise workstations in Project 03.

---

## Verification Performed

The following items were successfully verified:

- Enterprise topology
- SVI status
- IPv4 routing table
- Existing VLAN structure
- Inter-VLAN connectivity
- ARP table
- IEEE 802.1Q trunk operation

Verification screenshots are available in the **Screenshots** directory.

---

## Skills Demonstrated

- Inter-VLAN Routing
- Multilayer Switching
- Switch Virtual Interfaces
- IPv4 Addressing
- Default Gateway Configuration
- Connected Route Verification
- VLAN Architecture
- IEEE 802.1Q Trunking
- Layer 3 Connectivity Verification
- Cisco IOS Configuration
- EVE-NG Network Simulation
- Network Troubleshooting
- Technical Documentation

---

## Result

Project 03 successfully introduced Inter-VLAN Routing into the NorthStar Enterprise Network.

HQ-MLS01 provides Layer 3 communication between the HR, Finance, and IT Data VLANs using dedicated SVIs. The departmental networks were successfully installed as directly connected routes, and Inter-VLAN communication was successfully verified while the existing Project 02 Layer 2 infrastructure remained operational.

The completed implementation provides the Layer 3 campus foundation for the additional networking technologies introduced in subsequent NorthStar projects.

---

## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio