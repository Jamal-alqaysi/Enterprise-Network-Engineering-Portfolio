
## Objective

Implement First Hop Redundancy Protocol (HSRP) within the Headquarters network to eliminate the default gateway as a single point of failure while preserving all enterprise services implemented in previous projects.

---

## Technical Requirements

- Configure HSRP on all Headquarters VLANs.
- Deploy HQ-MLS01 as the Active HSRP gateway.
- Deploy HQ-MLS02 as the Standby HSRP gateway.
- Use a virtual IP address as the default gateway for all clients.
- Enable HSRP preemption to allow the preferred gateway to automatically resume the Active role after recovery.
- Maintain compatibility with the existing OSPF, DHCP, NAT, ACL, EtherChannel, Rapid PVST+, and IPv6 implementations.
- Verify HSRP failover and recovery.

---

## Scope

This project introduces only First Hop Redundancy Protocol (HSRP).

The existing enterprise topology, IPv4 and IPv6 addressing plans, OSPFv2, OSPFv3, NAT, ACLs, EtherChannel, and Rapid PVST+ remain unchanged. The Headquarters DHCP configuration is updated only as required to distribute the HSRP virtual gateway addresses. HQ-MLS02 is upgraded only to the extent required to participate in HSRP as the Standby default gateway.