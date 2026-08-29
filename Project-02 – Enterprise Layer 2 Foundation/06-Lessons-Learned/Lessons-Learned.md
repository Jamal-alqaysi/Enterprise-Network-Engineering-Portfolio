
## Overview

Project 02 expanded the NorthStar Enterprise Network by introducing a structured Layer 2 architecture based on VLAN segmentation, Voice VLANs, IEEE 802.1Q trunking, redundant Layer 2 connectivity, and Rapid PVST+.

The project demonstrated how enterprise switching technologies can be used to logically separate Data, Voice, and Management traffic while maintaining connectivity across a redundant Layer 2 infrastructure.

---

## Key Lessons

- VLANs provide an effective method for logically segmenting enterprise traffic across a shared switching infrastructure.
- Dedicated Voice VLANs allow Data and Voice traffic to remain logically separated while sharing the same physical access ports.
- IEEE 802.1Q trunks allow multiple VLANs to extend across interconnected enterprise switches.
- A dedicated Management VLAN provides a structured approach for network device administration.
- Using a dedicated Native VLAN avoids relying on VLAN 1 for enterprise trunk operation.
- Redundant Layer 2 links improve network resiliency but require Spanning Tree to prevent switching loops.
- Rapid PVST+ provides predictable Layer 2 loop prevention and supports deterministic root bridge selection.
- Selecting primary and secondary STP root bridges provides greater control over Layer 2 forwarding paths.
- Layer 2 segmentation can be implemented independently before introducing Inter-VLAN Routing.
- Configuration backups are essential when working with virtual network laboratories.
- Exporting device configurations after major implementation phases reduces the risk of losing completed work if the lab environment must be recreated.

---

## Project Outcome

Project 02 successfully established the Enterprise Layer 2 Foundation of the NorthStar Enterprise Network.

HQ-MLS02 and six Cisco IP Phones were added to the existing infrastructure, while departmental Data VLANs, dedicated Voice VLANs, a Management VLAN, a Native VLAN, IEEE 802.1Q trunking, redundant Layer 2 connectivity, and Rapid PVST+ were successfully implemented and verified.

The completed Layer 2 infrastructure provides the foundation required for Inter-VLAN Routing introduced in Project 03 and for the additional enterprise technologies implemented in subsequent NorthStar projects.