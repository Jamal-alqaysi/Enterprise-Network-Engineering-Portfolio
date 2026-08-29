
## Overview

This section describes the implementation process used to introduce Inter-VLAN Routing into the existing Enterprise Layer 2 infrastructure.

The physical topology and Layer 2 architecture established in Project 02 are retained. The implementation focuses on enabling Layer 3 communication between the existing departmental Data VLANs.

Cisco IOS configuration commands are documented separately in the **Configurations** directory.

---

## Step 1 – Verify the Existing Layer 2 Infrastructure

Before introducing Layer 3 functionality, the existing Enterprise Layer 2 infrastructure was verified.

The following components were confirmed operational:

- VLANs
- IEEE 802.1Q trunk links
- Management VLAN
- Voice VLANs
- Rapid PVST+
- Layer 2 connectivity

No changes were made to the physical topology.

---

## Step 2 – Enable Layer 3 Routing

Layer 3 routing was enabled on HQ-MLS01 to allow communication between the existing departmental Data VLANs.

HQ-MLS02 remained part of the Distribution Layer but did not participate in Inter-VLAN Routing during this project.

---

## Step 3 – Configure Switch Virtual Interfaces (SVIs)

Switch Virtual Interfaces were configured for the HR, Finance, and IT Data VLANs.

Each SVI was assigned the default gateway address for its corresponding departmental subnet.

The existing Management VLAN 99 remained dedicated to network device management.

---

## Step 4 – Configure End-User IPv4 Addressing

Static IPv4 addresses and default gateways were configured on all end-user PCs.

Each workstation was assigned an IPv4 address within its departmental subnet and configured to use the corresponding SVI on HQ-MLS01 as its default gateway.

---

## Step 5 – Verify Inter-VLAN Routing

Connectivity testing was performed to verify:

- Local VLAN communication
- Inter-VLAN communication
- Default gateway reachability
- SVI operational status
- Routing table entries

The implementation was considered successful after the required verification tests passed.

---

## Implementation Summary

Project 03 successfully introduced Inter-VLAN Routing without changing the existing physical topology or redesigning the Layer 2 infrastructure established in Project 02.

HQ-MLS01 provides Layer 3 communication between the HR, Finance, and IT Data VLANs through dedicated SVIs, while the existing Layer 2 services remain operational.

Detailed Cisco IOS configuration commands are stored in the **Configurations** directory.