
## Overview

Project 09 demonstrated how First Hop Redundancy Protocol (HSRP) can be introduced into an existing enterprise network to provide default gateway redundancy while preserving the infrastructure and services implemented in previous projects.

The implementation provided practical experience with HSRP virtual gateways, Active and Standby gateway roles, preemption, DHCP gateway integration, and failover and recovery validation.

---

## Key Lessons

- HSRP provides default gateway redundancy by allowing multiple Layer 3 devices to share a virtual IP address that clients use as their default gateway.
- HSRP Active and Standby roles determine which multilayer switch is responsible for forwarding traffic through the virtual gateway.
- HSRP priorities can be used to establish a preferred Active gateway, with HQ-MLS01 configured at priority 110 and HQ-MLS02 at priority 100.
- Preemption allows the preferred gateway to resume the Active role after recovery.
- Both multilayer switches require the necessary Layer 3 SVIs before they can participate in HSRP for the Headquarters VLANs.
- DHCP must distribute the HSRP virtual IP address rather than the physical SVI address of an individual multilayer switch.
- Introducing gateway redundancy requires coordination with existing enterprise services such as DHCP, ACLs, routing, and VLAN infrastructure.
- Problems involving previously implemented services can affect the successful integration and validation of a new technology and must be resolved as part of the implementation process.
- Verifying HSRP status, virtual gateway addressing, DHCP gateway assignment, and end-to-end connectivity provides a structured method for validating an HSRP deployment.
- Failover and failback testing is important to confirm that the Standby gateway can assume the Active role and that the preferred gateway can resume its role after recovery.
- In this project, HSRP failover and failback were specifically validated for VLAN 10.

---

## Project Outcome

Project 09 successfully introduced HSRP-based first-hop redundancy into the Headquarters network.

HQ-MLS01 operates as the preferred Active gateway and HQ-MLS02 as the Standby gateway for VLANs 10, 20, 30, and 99. Clients use HSRP virtual IP addresses as their default gateways, with the Headquarters DHCP configuration updated to distribute the corresponding virtual gateway addresses.

HSRP failover and failback were successfully validated for VLAN 10, confirming the expected gateway role transition and recovery behavior while preserving the same virtual default gateway address.