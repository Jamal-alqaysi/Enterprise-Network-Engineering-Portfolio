
## Overview

Project 01 was implemented in EVE-NG using a structured deployment sequence to establish the initial NorthStar Enterprise Network infrastructure.

The implementation focused on building the physical topology, applying the initial device configuration, assigning IPv4 addresses, enabling secure device management, and validating connectivity across the single-subnet environment.

---

## Deployment Sequence

### Step 1 – Build the Network Topology

- Deploy one Headquarters multilayer switch.
- Deploy three enterprise access switches.
- Deploy six enterprise workstations.
- Connect all devices according to the approved physical topology.
- Verify that all required network links are operational.

---

### Step 2 – Apply Initial Device Configuration

- Configure device hostnames.
- Apply the initial device management settings.
- Configure local administrative access.
- Enable secure SSH remote management.
- Configure the management IPv4 interface on HQ-MLS01.
- Save the device configurations.

---

### Step 3 – Configure End Devices

- Assign static IPv4 addresses to all enterprise workstations.
- Configure the `/24` subnet mask.
- Verify that all workstations are operating within the `192.168.0.0/24` network.

No default gateway is required for workstation communication in Project 01 because all end devices operate within the same IPv4 subnet.

---

### Step 4 – Validate the Initial Infrastructure

- Verify the operational status of network interfaces.
- Verify workstation IPv4 addressing.
- Verify connectivity between enterprise workstations.
- Verify connectivity between workstations and the HQ-MLS01 management interface.
- Verify SSH configuration and remote management functionality.
- Save the final device configurations.

---

## Implementation Notes

Project 01 establishes the initial network baseline without introducing VLAN segmentation, routing, redundancy, or advanced enterprise services.

Detailed Cisco IOS commands and device configurations are stored exclusively in the **Configurations** directory.