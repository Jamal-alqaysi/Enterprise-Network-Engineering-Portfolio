
## Overview

During the implementation and validation of Project 09, several issues were identified and resolved before the HSRP deployment could be successfully completed.

Some issues were directly related to the HSRP implementation, while others involved existing enterprise services from previous projects that affected the successful integration and validation of gateway redundancy.

Resolving these issues ensured that the existing network services remained operational while HSRP was introduced into the Headquarters network.

---

## Issue 1 – HQ-MLS02 Missing SVIs

### Problem

HQ-MLS02 initially operated as a Layer 2 switch and did not contain the Layer 3 VLAN interfaces required to participate in HSRP.

### Resolution

Layer 3 routing was enabled on HQ-MLS02, and SVIs were configured for VLANs 10, 20, 30, and 99.

Each SVI was assigned an individual IPv4 address within its corresponding subnet before HSRP was configured.

This allowed HQ-MLS02 to participate as the Standby HSRP gateway for the Headquarters VLANs.

---

## Issue 2 – DHCP Default Gateway

### Problem

After HSRP was introduced, DHCP clients continued receiving the physical HQ-MLS01 SVI address as their default gateway instead of the HSRP virtual gateway.

This prevented clients from fully using the redundant default gateway design introduced in Project 09.

### Resolution

The Headquarters DHCP pools were updated to replace the previous physical default gateway addresses with the corresponding HSRP virtual IP addresses.

The updated gateways were:

| VLAN | Previous Gateway | HSRP Virtual Gateway |
|------|------------------|----------------------|
| 10 | 192.168.10.1 | 192.168.10.254 |
| 20 | 192.168.20.1 | 192.168.20.254 |
| 30 | 192.168.30.1 | 192.168.30.254 |
| 99 | 192.168.99.1 | 192.168.99.254 |

Client addressing was then verified to confirm that the HSRP virtual gateway was being distributed correctly.

---

## Issue 3 – Branch DHCP Communication

### Problem

During Project 09 validation, DHCP communication from the branch networks was affected by the existing branch ACL configuration.

The ACLs prevented the required DHCP traffic from passing correctly, affecting the operation of an existing enterprise service needed for successful end-to-end validation.

### Resolution

The branch ACL configuration was updated to permit the required DHCP client and server traffic while preserving the existing security policy.

The required DHCP permits were placed before the restrictive ACL entries so DHCP communication could operate correctly without removing the intended branch access restrictions.

After the ACL adjustment, DHCP communication was restored and enterprise connectivity could be validated.

---

## Issue 4 – Incorrect ACL Applied on BR2

### Problem

During validation, the ACL intended for the BR1 LAN was found to be applied to the BR2 LAN interface.

This resulted in an incorrect branch security policy being applied on BR2 and affected the expected enterprise connectivity.

### Resolution

The incorrect ACL was removed from the BR2 LAN interface and replaced with the correct BR2-specific policy.

The correction restored the intended BR2 access-control behavior and allowed branch connectivity to be successfully validated.

---

## Troubleshooting Summary

The issues encountered during Project 09 included both HSRP-specific implementation requirements and problems involving existing enterprise services that affected successful project integration and validation.

HQ-MLS02 was prepared for Layer 3 gateway redundancy by configuring the required SVIs, and the Headquarters DHCP pools were updated to distribute the HSRP virtual gateway addresses.

Existing branch DHCP and ACL issues encountered during validation were also corrected so that the previously implemented enterprise services operated correctly alongside the new HSRP deployment.

After resolving these issues, HSRP operation, DHCP gateway assignment, enterprise connectivity, and VLAN 10 failover and failback were successfully validated.