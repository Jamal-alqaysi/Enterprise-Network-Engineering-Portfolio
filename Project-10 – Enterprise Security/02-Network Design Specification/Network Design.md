
## Design Overview

Project 10 builds directly on the enterprise infrastructure implemented in Project 09. The existing enterprise topology, VLAN architecture, IP addressing, gateway redundancy, routing, and network services remain unchanged.

This project strengthens the security of the enterprise access layer by introducing Layer 2 security features on all access switches where end-user devices connect to the network. The security design protects the network against unauthorized device access, rogue DHCP servers, ARP spoofing, spanning-tree manipulation, and excessive Layer 2 traffic while preserving existing enterprise connectivity and services.

The distribution layer continues to provide Layer 3 services, HSRP gateway redundancy, routing, and inter-switch connectivity established in previous projects. Security enhancements are introduced at the access layer without modifying the existing enterprise architecture.

---

## Security Design

The original Layer 2 security design includes the following technologies:

- Port Security
- Sticky MAC Address Learning
- DHCP Snooping
- Dynamic ARP Inspection (DAI)
- Storm Control
- PortFast
- BPDU Guard

During implementation, Dynamic ARP Inspection (DAI) and Storm Control could not be deployed using the Cisco IOL images available in the EVE-NG lab environment.

As a result, the final implemented Layer 2 security design consists of:

- Port Security
- Sticky MAC Address Learning
- DHCP Snooping
- PortFast
- BPDU Guard

This distinction preserves the original security design while accurately documenting the capabilities implemented and validated in the lab environment.

---

## Distribution Layer

HQ-MLS01 and HQ-MLS02 continue to provide the enterprise Layer 3 services, HSRP gateway redundancy, inter-VLAN routing, dynamic routing, and inter-switch connectivity implemented in previous projects.

No architectural changes are introduced to the distribution layer as part of this project.

---

## Access Layer

Layer 2 security features are deployed on all Headquarters and Branch access switches.

The final access-layer implementation includes:

- Port Security
- Sticky MAC Address Learning
- DHCP Snooping
- PortFast
- BPDU Guard

DHCP Snooping is enabled on all enterprise access switches. Trusted interfaces are configured on the uplink connections toward the distribution layer or branch routers, while all user-facing access ports remain untrusted.

Port Security is applied to all user-facing access ports to limit each interface to a single authorized device using Sticky MAC Address learning.

PortFast and BPDU Guard are enabled on all user-facing access ports to protect the spanning-tree topology while maintaining fast workstation connectivity.

Dynamic ARP Inspection (DAI) and Storm Control remain part of the original security design but are not included in the final access-layer configuration because of the limitations of the Cisco IOL images used in the EVE-NG lab environment.

---

## Network Topology

The physical enterprise topology remains identical to Project 09.

![Figure 1. Enterprise Security Topology](../Assets/Figure%201.%20Enterprise%20Security%20Topology.png)

No additional network devices or physical connections are introduced in this project.