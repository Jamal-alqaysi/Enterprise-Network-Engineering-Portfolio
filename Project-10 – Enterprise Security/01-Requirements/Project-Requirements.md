
## Objective

Implement Layer 2 security controls across the enterprise access layer to strengthen network security while preserving the existing enterprise architecture and services implemented in previous projects.

---

## Technical Requirements

- Implement Port Security on all user-facing access ports.
- Enable Sticky MAC Address learning to dynamically secure authorized end devices.
- Limit each secured access port to a maximum of one learned MAC address.
- Configure Port Security violation mode as restrict.
- Enable DHCP Snooping across the enterprise access layer.
- Configure uplink interfaces as trusted DHCP Snooping ports while keeping user-facing access ports untrusted.
- Enable PortFast on all user-facing access ports.
- Enable BPDU Guard on all user-facing access ports.
- Implement Dynamic ARP Inspection (DAI) to protect against ARP spoofing attacks.
- Implement Storm Control to protect access ports against excessive broadcast, multicast, and unknown unicast traffic.
- Apply Layer 2 security policies across Headquarters and Branch access switches.
- Maintain compatibility with the existing VLAN, EtherChannel, Rapid PVST+, HSRP, OSPF, DHCP, NAT, ACL, IPv4, and IPv6 implementations.
- Verify Layer 2 security operation and enterprise connectivity after applying the security policies.

---

## Scope

Project 10 focuses exclusively on strengthening security at the enterprise access layer.

The existing physical topology, VLAN architecture, IPv4 and IPv6 addressing, Layer 3 gateway design, routing architecture, HSRP, DHCP, NAT, ACL, EtherChannel, and Rapid PVST+ implementations remain unchanged.

The planned Layer 2 security scope includes Port Security, Sticky MAC Address Learning, DHCP Snooping, PortFast, BPDU Guard, Dynamic ARP Inspection (DAI), and Storm Control.

During implementation, Dynamic ARP Inspection (DAI) and Storm Control could not be deployed using the Cisco IOL images available in the EVE-NG lab environment. These features therefore remain part of the original security design but are excluded from the final implemented configuration.

The final implemented security controls consist of Port Security, Sticky MAC Address Learning, DHCP Snooping, PortFast, and BPDU Guard across the enterprise access layer.