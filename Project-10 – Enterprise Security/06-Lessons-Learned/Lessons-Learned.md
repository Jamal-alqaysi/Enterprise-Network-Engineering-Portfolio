
## Overview

Project 10 enhanced the security of the NorthStar Enterprise Network by introducing Layer 2 security mechanisms at the enterprise access layer while preserving the existing enterprise architecture.

The implementation demonstrated how security controls can be applied to user-facing access ports while maintaining connectivity across the tested enterprise network.

---

## Key Lessons

- Layer 2 security should be implemented primarily at the enterprise access layer where end-user devices connect to the network.
- Port Security can restrict unauthorized devices by limiting each secured access port to a defined number of learned MAC addresses.
- Sticky MAC Address Learning provides a practical method for dynamically learning and securing authorized device MAC addresses on access ports.
- DHCP Snooping protects the access layer from rogue DHCP servers by establishing trusted and untrusted interface boundaries.
- Dynamic ARP Inspection depends on reliable DHCP Snooping binding information for dynamic ARP validation.
- PortFast allows user-facing access ports to transition quickly to the forwarding state for connected end devices.
- BPDU Guard protects the spanning-tree topology by disabling protected access ports if unexpected BPDUs are received.
- Dynamic ARP Inspection and Storm Control demonstrated that virtual lab platforms may not support every planned enterprise security feature.
- Platform limitations should be identified, tested, and documented rather than being treated as configuration errors.
- Excluding a feature that cannot be reliably implemented or validated is preferable to documenting an unsupported configuration as successfully deployed.

---

## Project Outcome

Project 10 successfully strengthened the enterprise access layer by implementing Port Security, Sticky MAC Address Learning, DHCP Snooping, PortFast, and BPDU Guard across the Headquarters and Branch access switches.

Dynamic ARP Inspection and Storm Control were evaluated as part of the original security plan but were excluded from the final configuration because of limitations encountered with the Cisco IOL lab environment.

The final implementation improved Layer 2 access security, and IPv4 connectivity between the tested Headquarters and Branch networks was successfully verified after the supported security controls were applied.