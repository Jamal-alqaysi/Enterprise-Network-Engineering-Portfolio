
# Project 02 – Implementation

## Overview

This section describes the deployment methodology used to implement the Enterprise Layer 2 Foundation introduced in Project 02.

The implementation follows a structured sequence to ensure that each Layer 2 technology is deployed and validated before proceeding to the next stage.

Cisco IOS configuration commands are intentionally excluded from this section and are documented separately in the **Configurations** directory.

---

## Implementation Sequence

The deployment was completed using the following implementation phases:

1. Build the updated enterprise topology in EVE-NG.
2. Add the secondary multilayer switch (HQ-MLS02).
3. Deploy six Cisco IP Phones.
4. Establish redundant uplinks between the Distribution and Access layers.
5. Create Data VLANs and Voice VLANs.
6. Configure IEEE 802.1Q trunk links.
7. Configure access ports for Data and Voice traffic.
8. Configure the Management and Native VLANs.
9. Enable Rapid PVST+.
10. Configure the primary and secondary root bridges.
11. Verify Layer 2 operation.
12. Document the completed implementation.

---

## Topology Deployment

The existing infrastructure from Project 01 was retained and expanded.

The following components were added:

- HQ-MLS02
- Six Cisco IP Phones
- Redundant Distribution Layer uplinks

No existing devices from Project 01 were removed.

---

## VLAN Deployment

Departmental Data VLANs were created to provide logical separation between user groups.

Dedicated Voice VLANs were introduced to support the Cisco IP Phones while maintaining logical separation between Voice and Data traffic.

Additional VLANs were created for network management and native trunk operation.

---

## Trunk Deployment

Switch-to-switch connections were configured as IEEE 802.1Q trunks.

The trunk infrastructure transports the required Data VLANs, Voice VLANs, Management VLAN, and Native VLAN throughout the enterprise Layer 2 network.

---

## Access Layer Deployment

User-facing switch ports were configured to support both enterprise workstations and Cisco IP Phones.

Each access port provides connectivity for Data and Voice traffic while maintaining logical separation through dedicated VLAN assignments.

---

## Spanning Tree Deployment

Rapid PVST+ was enabled across the enterprise Layer 2 topology.

The root bridge hierarchy was intentionally defined by assigning:

- HQ-MLS01 as the Primary Root Bridge
- HQ-MLS02 as the Secondary Root Bridge

This configuration provides deterministic Layer 2 forwarding while preventing switching loops across the redundant links.

---

## Verification Preparation

After implementation was completed, verification tests were performed to confirm:

- VLAN creation
- Voice VLAN operation
- IEEE 802.1Q trunk operation
- Root bridge election
- Layer 2 connectivity
- Loop-free topology

The verification results are documented in the **Verification** section.

---

## Implementation Summary

Project 02 successfully established the Enterprise Layer 2 Foundation by implementing redundant Distribution Layer connectivity, VLAN segmentation, Voice VLANs, IEEE 802.1Q trunking, and Rapid PVST+.

The completed implementation provides the Layer 2 foundation required for the enterprise technologies introduced in subsequent NorthStar projects.