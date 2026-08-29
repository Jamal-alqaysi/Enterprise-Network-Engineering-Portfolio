
## Objective

Improve the reliability of the enterprise Layer 2 infrastructure by introducing EtherChannel between the Headquarters multilayer switches and using Rapid PVST+ to maintain a loop-free switching topology.

---

## Requirements

- Preserve the existing enterprise topology and IP addressing.
- Preserve all VLANs and services implemented in previous projects.
- Implement EtherChannel using LACP between HQ-MLS01 and HQ-MLS02.
- Configure the EtherChannel as an IEEE 802.1Q trunk.
- Preserve the existing native VLAN and configure the required enterprise VLANs across the EtherChannel trunk.
- Configure Rapid PVST+ on the Headquarters switching infrastructure.
- Configure a deterministic Root Bridge for all enterprise VLANs.
- Verify EtherChannel formation and member-port status.
- Verify trunk operation across the Port-Channel.
- Verify Rapid PVST+ root bridge election and port roles.
- Verify continued operation of all enterprise services.

---

## Expected Outcome

At the end of this project, HQ-MLS01 and HQ-MLS02 will be connected through a redundant logical EtherChannel trunk using LACP.

Rapid PVST+ will maintain a stable and loop-free Layer 2 topology while all services implemented in Projects 01 through 06 continue to operate without modification.