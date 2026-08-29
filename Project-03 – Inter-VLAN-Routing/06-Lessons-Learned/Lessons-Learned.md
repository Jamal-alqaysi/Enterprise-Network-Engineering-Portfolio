
## Overview

Project 03 introduced Layer 3 functionality into the existing Enterprise Layer 2 infrastructure without modifying the physical topology.

The implementation demonstrated how multilayer switching enables communication between isolated VLANs while preserving the existing Layer 2 design.

---

## Key Lessons

- Switch Virtual Interfaces (SVIs) provide an efficient method for implementing Inter-VLAN Routing on a multilayer switch.
- A multilayer switch can perform both Layer 2 switching and Layer 3 routing within the same device.
- Each VLAN requires a unique default gateway to enable communication with other VLANs.
- Layer 3 routing enables forwarding between directly connected VLANs.
- Existing Layer 2 services, including IEEE 802.1Q trunking and Rapid PVST+, continue to operate after Layer 3 routing is introduced.
- Verifying SVI status, routing tables, and end-to-end connectivity confirms successful Inter-VLAN Routing deployment.

---

## Project Outcome

Project 03 successfully introduced Inter-VLAN Routing while preserving the Enterprise Layer 2 foundation established in Project 02.

The network now supports communication between departmental VLANs and provides the foundation for the routing and connectivity technologies introduced in subsequent projects.