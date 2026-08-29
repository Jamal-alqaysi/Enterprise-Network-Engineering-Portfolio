
## Overview

Project 07 demonstrated how Layer 2 redundancy technologies can improve network availability and stability without modifying the existing Layer 3 infrastructure or enterprise services.

The implementation of EtherChannel and Rapid PVST+ provided practical experience with link aggregation, spanning-tree optimization, and redundant Layer 2 design.

---
## Key Lessons

- EtherChannel combines multiple physical links into a single logical connection, increasing available bandwidth and providing link redundancy.
- LACP provides a standards-based method for dynamically forming and maintaining EtherChannel links.
- EtherChannel member interfaces must use consistent Layer 2 parameters to successfully form the logical Port-Channel.
- Configuring the Port-Channel as a trunk allows multiple VLANs to traverse the aggregated link.
- Native VLAN and allowed VLAN configurations must remain consistent across both sides of the trunk.
- Rapid PVST+ provides faster convergence than traditional STP while maintaining a loop-free Layer 2 topology.
- Configuring a deterministic Root Bridge provides predictable Layer 2 forwarding paths.
- A secondary Root Bridge provides a controlled spanning-tree fallback if the primary Root Bridge becomes unavailable.
- EtherChannel and Rapid PVST+ complement each other by providing both link redundancy and loop prevention.
- Verifying Layer 2 redundancy independently before performing end-to-end connectivity testing simplifies validation and troubleshooting.

---
## Project Outcome

Project 07 successfully improved the Layer 2 resiliency of the NorthStar Enterprise Network by implementing LACP EtherChannel and Rapid PVST+.

The resulting design provides increased link availability, improved bandwidth utilization, deterministic spanning-tree operation, and a stable loop-free Layer 2 topology while preserving all enterprise services implemented in previous projects.