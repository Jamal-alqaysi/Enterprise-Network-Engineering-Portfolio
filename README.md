
# NorthStar Enterprise Network

### Enterprise Network Engineering Portfolio

![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Projects](https://img.shields.io/badge/Projects-12-blue)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Vendor](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)
![Network](https://img.shields.io/badge/Network-IPv4%20%7C%20IPv6-blueviolet)
![Linux](https://img.shields.io/badge/OS-Linux-FCC624)
![Python](https://img.shields.io/badge/Language-Python_3-3776AB)
![Netmiko](https://img.shields.io/badge/Automation-Netmiko-28A745)  
  
---
## Overview

**NorthStar Enterprise Network** is a multi-site enterprise networking lab designed, implemented, verified, and documented using Cisco technologies in EVE-NG.

The portfolio consists of **12 completed cumulative projects** that progressively develop a basic enterprise infrastructure into a redundant dual-stack enterprise network with Python-based network automation.

Rather than presenting isolated networking labs, each project builds directly on the infrastructure established in previous projects while introducing a focused networking concept.

The portfolio demonstrates practical experience in:

- Enterprise network design
- Routing and switching
- IPv4 and IPv6 networking
- Dynamic routing
- Network services
- Layer 2 and Layer 3 redundancy
- Access-layer security
- Python network automation
- Network verification
- Troubleshooting
- Technical documentation

---
# Project Roadmap

|Project|Title|Primary Focus|Status|
|---|---|---|---|
|**01**|Core Infrastructure Deployment|Enterprise Network Foundation|✅|
|**02**|Enterprise Layer 2 Foundation|VLANs & 802.1Q Trunking|✅|
|**03**|Inter-VLAN Routing|Layer 3 Switching & SVIs|✅|
|**04**|WAN Connectivity & Static Routing|Multi-Site WAN Connectivity|✅|
|**05**|Dynamic Routing Implementation (OSPF)|OSPFv2 Dynamic Routing|✅|
|**06**|DHCP, NAT & ACL Services|Enterprise Network Services|✅|
|**07**|Layer 2 Redundancy|EtherChannel & Rapid PVST+|✅|
|**08**|IPv6 Enterprise Network|Dual-Stack IPv4/IPv6 & OSPFv3|✅|
|**09**|First Hop Redundancy|HSRP|✅|
|**10**|Enterprise Security|Layer 2 Access Security|✅|
|**11**|Enterprise Campus Network|Final Integration & Layer 3 Redundancy|✅|
|**12**|Network Automation|Python & Netmiko|✅|

---
# Network Evolution

The NorthStar Enterprise Network follows a progressive enterprise deployment model:

```
Core Infrastructure
        │
        ▼
VLAN Segmentation
        │
        ▼
Inter-VLAN Routing
        │
        ▼
WAN Connectivity
        │
        ▼
OSPF Dynamic Routing
        │
        ▼
DHCP • NAT/PAT • ACLs
        │
        ▼
Layer 2 Redundancy
        │
        ▼
IPv6 • OSPFv3
        │
        ▼
HSRP Gateway Redundancy
        │
        ▼
Layer 2 Security
        │
        ▼
Final Enterprise Integration
        │
        ▼
Python Network Automation
```

Each stage preserves the existing infrastructure while introducing and validating the technologies required for the next stage.

Project 12 extends the completed enterprise network by introducing SSH-based network automation without modifying the existing architecture or services.

---
# Final Enterprise Architecture

By Project 11, the NorthStar Enterprise Network evolved into a redundant multi-site, dual-stack enterprise environment.

Project 12 extends this infrastructure with basic Python-based network automation for operational verification and device management.

The final architecture includes:

### Headquarters Infrastructure

- Redundant multilayer switches
- Redundant edge routers
- Multiple enterprise VLANs
- Inter-VLAN Routing
- HSRP redundant default gateways
- EtherChannel connectivity
- Rapid PVST+ Layer 2 redundancy
### Branch Connectivity

- Two branch networks
- Primary and backup WAN paths
- Dynamic route learning
- Automatic routing failover
### Routing

- IPv4 routing
- IPv6 routing
- OSPFv2
- OSPFv3
- Preferred and backup routing paths
- OSPF cost-based path selection
- Layer 3 route convergence
### Enterprise Services

- DHCP
- DHCP Relay
- NAT/PAT
- Access Control Lists
- Simulated Internet connectivity
### Layer 2 Security

- Port Security
- Sticky MAC Address Learning
- DHCP Snooping
- PortFast
- BPDU Guard

### Network Management & Automation

- SSH-based administrative access
- Dedicated Linux management workstation
- Centralized management through the Management VLAN
- Python 3 and Netmiko
- Automated Cisco IOS command execution
- Network interface status analysis
- Multi-device SSH automation
- Basic error handling and session management

---
# Technologies Demonstrated

| Routing & Layer 3      | Switching & Layer 2       | Services & Security   |
| ---------------------- | ------------------------- | --------------------- |
| IPv4 Routing           | VLANs                     | DHCP                  |
| IPv6 Routing           | 802.1Q Trunking           | DHCP Relay            |
| Static Routing         | Voice VLANs               | NAT/PAT               |
| OSPFv2                 | Inter-VLAN Routing        | Access Control Lists  |
| OSPFv3                 | Switch Virtual Interfaces | Port Security         |
| HSRP                   | Rapid PVST+               | Sticky MAC            |
| OSPF Cost Manipulation | LACP EtherChannel         | DHCP Snooping         |
| Route Failover         | Layer 2 Redundancy        | PortFast / BPDU Guard |

### Network Automation

- Python 3
- Netmiko
- SSH Automation
- Python Lists and Dictionaries
- Loops and Conditional Statements
- String Processing
- Exception Handling
- Multi-Device Command Execution

### Platforms & Tools

- Cisco IOS
- Cisco IOL
- EVE-NG
- Linux
- Python 3
- Netmiko
- Cisco CLI
- SSH
---

# Documentation Methodology

Each project follows a consistent engineering documentation structure:

```
Project-XX/
│
├── 01-Requirements/
├── 02-Network-Design-Specification/
├── 03-Implementation/
├── 04-Verification/
├── 05-Troubleshooting/
├── 06-Lessons-Learned/
├── Assets/
├── Configurations/
├── Screenshots/
└── README.md
```

### Requirements

Defines the objectives, technical requirements, and scope of the project.

### Network Design Specification

Documents the architecture, addressing, VLAN design, routing design, automation topology, and relevant technical decisions.

### Implementation

Describes the deployment methodology and implementation sequence.

Cisco IOS commands and Python scripts are intentionally excluded from the Implementation documentation.

### Verification

Documents the tests performed to validate the technologies introduced in each project.

### Troubleshooting

Documents actual technical issues encountered during implementation or validation, including their causes and resolutions.

### Lessons Learned

Summarizes the primary technical and practical lessons gained from each project.

### Configurations

Contains the Cisco IOS configuration additions or modifications introduced throughout Projects 01–11.

Each network configuration project includes:

```
1. Configuration-Scope
```

which defines the configuration scope for that specific project.

Project 12 contains the Python automation script used for SSH-based network verification.

### Assets

Contains network topology diagrams, automation topology diagrams, and other design graphics.

### Screenshots

Contains CLI outputs, EVE-NG topology captures, connectivity tests, Python automation results, and other verification evidence.

---

# Repository Structure

```
Enterprise-Network-Engineering-Portfolio/
│
├── Project-01 – Core Infrastructure Deployment/
├── Project-02 – Enterprise Layer 2 Foundation/
├── Project-03 – Inter-VLAN-Routing/
├── Project-04 – WAN Connectivity & Static Routing/
├── Project-05 – Dynamic Routing Implementation (OSPF)/
├── Project-06 – DHCP, NAT & ACL Services/
├── Project-07 – Layer 2 Redundancy (EtherChannel & Rapid PVST+)/
├── Project-08 – IPv6 Enterprise Network/
├── Project-09 – First Hop Redundancy (HSRP)/
├── Project-10 – Enterprise Security/
├── Project-11 – Enterprise Campus Network/
├── Project-12 – Network Automation/
└── README
```

---

# Verification Philosophy

The portfolio emphasizes **evidence-based implementation**.

Technologies introduced throughout the projects are validated using appropriate operational verification such as:

- Interface and VLAN status
- 802.1Q trunk operation
- Inter-VLAN connectivity
- Routing-table inspection
- OSPF neighbor relationships
- OSPF route learning
- IPv4 and IPv6 connectivity
- DHCP address allocation
- NAT/PAT operation
- ACL behavior
- EtherChannel status
- Spanning Tree operation
- HSRP gateway redundancy
- Layer 2 security verification
- Routing failover
- SSH management connectivity
- Automated Cisco IOS command execution
- Interface status analysis using Python
- Multi-device network automation
- Basic exception handling and SSH session management

Supporting evidence is maintained within the individual project directories.

---

# Key Skills Demonstrated

**Network Design**

Designing and progressively expanding a multi-site enterprise network.

**Routing & Switching**

Implementing Layer 2 switching, Layer 3 switching, static routing, OSPFv2, OSPFv3, and redundant routing paths.

**High Availability**

Implementing Layer 2, default-gateway, WAN, and Layer 3 routing redundancy.

**Network Services**

Deploying DHCP, DHCP Relay, NAT/PAT, and traffic-control policies.

**Network Security**

Implementing access-layer security and Access Control Lists.

**IPv6 Networking**

Integrating IPv6 into an existing IPv4 environment using a dual-stack architecture.

**Network Automation**

Using Python and Netmiko to establish SSH connections, execute Cisco IOS commands, retrieve interface information, and automate operational verification across multiple network devices.

**Troubleshooting & Verification**

Diagnosing implementation issues and validating network operation using Cisco IOS operational commands, Python automation, and end-to-end testing.

**Technical Documentation**

Maintaining structured requirements, design specifications, implementation methodology, verification evidence, troubleshooting records, lessons learned, and configuration documentation.

---

# Portfolio Objective

The objective of the NorthStar Enterprise Network portfolio is to demonstrate practical enterprise networking knowledge through a structured and cumulative laboratory environment.

Instead of presenting independent networking exercises, the portfolio demonstrates how multiple enterprise technologies can be progressively integrated into a larger architecture while maintaining network continuity, redundancy, verification evidence, and consistent technical documentation.

The final project extends this experience by introducing Python-based network automation using Netmiko for basic operational verification and multi-device management tasks.

---

## Author

**Jamal Al Qaysi**

Enterprise Network Engineering Portfolio