
## Overview

Project 01 established the foundational infrastructure of the NorthStar Enterprise Network and demonstrated the importance of building and validating a stable network baseline before introducing more advanced enterprise technologies.

The project provided practical experience with physical topology deployment, basic Cisco device configuration, IPv4 addressing, Layer 2 connectivity, and secure network device management within the EVE-NG environment.

---

## Key Lessons

- A stable physical and logical network foundation should be established before introducing advanced enterprise technologies.
- Hierarchical network design provides a structured approach for organizing enterprise switching infrastructure.
- Consistent device naming simplifies network identification, management, documentation, and future expansion.
- A structured IPv4 addressing plan improves network organization and prepares the infrastructure for future segmentation.
- Devices operating within the same IPv4 subnet can communicate directly without requiring a Layer 3 default gateway.
- Basic interface verification should be completed before performing end-to-end connectivity testing.
- ICMP testing provides a simple and effective method for validating connectivity between enterprise end devices.
- SSH provides secure remote administrative access to Cisco network devices and should be preferred over insecure management protocols such as Telnet.
- Virtual lab devices such as VPCS may have functional limitations that should be distinguished from actual network configuration problems.
- Establishing a clean and verified baseline simplifies the implementation and troubleshooting of technologies introduced in subsequent projects.

---

## Project Outcome

Project 01 successfully established the initial infrastructure of the NorthStar Enterprise Network.

One Headquarters multilayer switch, three enterprise access switches, and six workstations were successfully deployed within the `192.168.0.0/24` IPv4 network. End-to-end Layer 2 connectivity was verified across the enterprise environment, and secure SSH management was configured on HQ-MLS01.

The completed infrastructure provides a stable and structured baseline for the enterprise networking technologies introduced throughout the subsequent NorthStar projects.