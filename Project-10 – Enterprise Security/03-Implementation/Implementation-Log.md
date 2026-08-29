
## Overview

Project 10 strengthens the security of the NorthStar Enterprise Network by implementing Layer 2 security features across the enterprise access layer while preserving the infrastructure and services introduced in previous projects.

The implementation focuses on protecting user-facing access ports against unauthorized network access, rogue DHCP servers, and spanning-tree attacks without modifying the existing enterprise topology or Layer 3 services.

Dynamic ARP Inspection (DAI) and Storm Control were also included in the original security plan. During implementation, these features could not be deployed using the Cisco IOL images available in the EVE-NG lab environment and were therefore excluded from the final configuration.

---

## Implementation Process

### Step 1 – Configure Port Security

Port Security is configured on user-facing access ports across the Headquarters and Branch access switches.

Each secured access port is limited to a single authorized device using Sticky MAC Address learning. Restrict mode is used for Port Security violations while allowing the interface to remain operational.

---

### Step 2 – Configure DHCP Snooping

DHCP Snooping is enabled across the enterprise access layer.

Uplink interfaces toward the distribution layer or branch routers are configured as trusted DHCP Snooping interfaces, while user-facing access ports remain untrusted to prevent unauthorized DHCP servers from providing addressing information to enterprise clients.

The existing Layer 3 architecture remains unchanged while DHCP Snooping is introduced at the access layer.

---

### Step 3 – Configure PortFast and BPDU Guard

PortFast is enabled on user-facing access ports to allow connected end devices to transition quickly to the forwarding state.

BPDU Guard is enabled on the protected access ports to prevent unauthorized switch connections from affecting the enterprise spanning-tree topology.

---

### Step 4 – Evaluate DAI and Storm Control

Dynamic ARP Inspection (DAI) and Storm Control were included in the original Layer 2 security plan and evaluated during implementation.

Dynamic ARP Inspection could not be reliably validated because the DHCP Snooping Binding Table did not populate as required for dynamic ARP validation. Storm Control could not be implemented because the required configuration commands were unavailable on the Cisco IOL Layer 2 image used in the EVE-NG lab environment.

As a result, DAI and Storm Control were excluded from the final implemented configuration.

The final Layer 2 security implementation therefore consists of Port Security, Sticky MAC Address Learning, DHCP Snooping, PortFast, and BPDU Guard.

---

### Step 5 – Verify Layer 2 Security

The implemented Layer 2 security features are verified to confirm their operation and validate enterprise connectivity after the security policies are applied.

The verification process includes:

- Port Security and Sticky MAC Address operation.
- DHCP Snooping operation and trusted/untrusted interface roles.
- PortFast and BPDU Guard configuration.
- IPv4 connectivity between the tested Headquarters and Branch networks.