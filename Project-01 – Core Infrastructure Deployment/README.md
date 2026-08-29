
# Project 01 – Core Infrastructure Deployment

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)

## Project Information

| Item | Value |
| --- | --- |
| Project | Project 01 – Core Infrastructure Deployment |
| Version | v1.0 |
| Status | Completed |
| Platform | EVE-NG |
| Vendor | Cisco |

---

## Overview

Project 01 establishes the foundational infrastructure of the **NorthStar Enterprise Network**.

The project deploys one Headquarters multilayer switch, three enterprise access switches, and six workstations within a single IPv4 network. Basic Cisco device configuration, management IPv4 addressing, secure SSH access, and end-to-end Layer 2 connectivity are implemented and verified.

The completed infrastructure provides the baseline for all subsequent projects in the Enterprise Network Engineering Portfolio.

---

## Objectives

- Build the initial NorthStar Enterprise Network infrastructure.
- Deploy one Headquarters multilayer switch.
- Deploy three enterprise access switches.
- Connect six enterprise workstations.
- Configure management IPv4 addressing.
- Configure static IPv4 addressing on enterprise workstations.
- Configure secure device management using SSH Version 2.
- Verify end-to-end Layer 2 connectivity.
- Establish the baseline infrastructure for subsequent enterprise networking projects.

---

## Technologies Used

- Cisco IOS 
- Cisco IOL Layer 3
- Cisco IOL Layer 2
- IPv4
- Layer 2 Switching
- SSH Version 2
- Local User Authentication
- EVE-NG
- Cisco IOS CLI
- Draw.io
- Markdown

---

## Project Structure

```text
Project-01-Core-Infrastructure-Deployment/
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
│   ├── HQ-MLS01
│   ├── HQ-SW01
│   ├── HQ-SW02
│   └── HQ-SW03
├── Screenshots
└── README
```

---

## Enterprise Network Topology

![Figure 1. Project 01 Core-Infrastructure-Topology](Assets/Figure%201.%20Project%2001%20Core-Infrastructure-Topology.png)

The initial enterprise topology consists of:

- HQ-MLS01 as the Distribution Layer multilayer switch.
- HQ-SW01, HQ-SW02, and HQ-SW03 as Access Layer switches.
- HR-PC01 and HR-PC02 representing Human Resources users.
- FIN-PC01 and FIN-PC02 representing Finance users.
- IT-PC01 and IT-PC02 representing Information Technology users.

All network management interfaces and enterprise workstations operate within the `192.168.0.0/24` IPv4 network.

This topology establishes the initial physical and logical foundation of the NorthStar Enterprise Network before segmentation, routing, redundancy, and additional enterprise services are introduced in subsequent projects.

---

## IPv4 Addressing

| Device | IPv4 Address | Subnet Mask |
| --- | --- | --- |
| HQ-MLS01 | 192.168.0.1 | 255.255.255.0 |
| HQ-SW01 | 192.168.0.2 | 255.255.255.0 |
| HQ-SW02 | 192.168.0.3 | 255.255.255.0 |
| HQ-SW03 | 192.168.0.4 | 255.255.255.0 |
| HR-PC01 | 192.168.0.10 | 255.255.255.0 |
| HR-PC02 | 192.168.0.11 | 255.255.255.0 |
| FIN-PC01 | 192.168.0.20 | 255.255.255.0 |
| FIN-PC02 | 192.168.0.21 | 255.255.255.0 |
| IT-PC01 | 192.168.0.30 | 255.255.255.0 |
| IT-PC02 | 192.168.0.31 | 255.255.255.0 |

---

## Verification Performed

The following items were successfully verified:

- Enterprise topology deployment
- HQ-MLS01 interface status
- Access switch interface status
- Management IPv4 addressing
- End device IPv4 configuration
- HQ-MLS01 management connectivity
- End-to-end enterprise connectivity
- SSH configuration

Verification screenshots are available in the **Screenshots** directory.

---

## Skills Demonstrated

- Enterprise Network Design
- Hierarchical Network Design
- Cisco IOS Configuration
- IPv4 Addressing
- Layer 2 Switching
- Management Interface Configuration
- Secure Device Management
- SSH Version 2
- Local User Authentication
- Network Connectivity Verification
- EVE-NG Network Simulation
- Network Troubleshooting
- Technical Documentation

---

## Result

Project 01 successfully established the foundational infrastructure of the NorthStar Enterprise Network.

One Headquarters multilayer switch, three enterprise access switches, and six workstations were successfully deployed within the `192.168.0.0/24` IPv4 network. Management addressing, secure SSH access, and end-to-end Layer 2 connectivity were successfully configured and verified.

The completed infrastructure provides a stable and structured baseline for the enterprise technologies introduced throughout the subsequent NorthStar projects.

---

## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio