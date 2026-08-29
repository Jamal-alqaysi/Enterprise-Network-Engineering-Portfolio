
# Project 11 – Final Enterprise Network Integration

## Objective

Integrate the enterprise technologies implemented throughout the previous projects into a resilient and redundant enterprise network while preserving the existing Headquarters and Branch architecture.

---

## Technical Requirements

- Integrate the network services and technologies implemented in previous projects into the final enterprise architecture.
- Preserve redundant default gateway services for the Headquarters VLANs using HSRP.
- Provide redundant Layer 3 paths between the Headquarters multilayer switches and edge routers.
- Provide redundant WAN paths between Headquarters and both Branch networks.
- Use OSPFv2 to provide dynamic IPv4 routing and automatic path failover.
- Configure primary and backup OSPFv2 paths using appropriate interface costs.
- Provide redundant IPv4 Internet connectivity through both Headquarters edge routers.
- Configure NAT/PAT on both Headquarters edge routers to support IPv4 Internet connectivity through either edge path.
- Extend IPv6 connectivity across the redundant Headquarters, WAN, Branch, and external network infrastructure.
- Use OSPFv3 to provide dynamic IPv6 routing across the redundant enterprise paths.
- Configure primary and backup OSPFv3 paths using appropriate interface costs.
- Maintain the existing VLAN, DHCP, ACL, EtherChannel, Rapid PVST+, and Layer 2 security implementations.
- Preserve secure administrative access using SSH.
- Provide a dedicated Linux management workstation for SSH-based administrative verification.
- Provide automatic routing failover across redundant IPv4 and IPv6 network paths.
- Provide end-to-end IPv4 and IPv6 connectivity across the integrated enterprise network.
- Verify routing convergence and recovery across the redundant network infrastructure.

---

## Scope

This project represents the final integration of the NorthStar Enterprise Network.

The existing enterprise VLAN architecture, IPv4 and IPv6 addressing plans, HSRP, OSPFv2, OSPFv3, DHCP, NAT/PAT, ACLs, EtherChannel, Rapid PVST+, Layer 2 security, and SSH implementations are preserved and integrated into the final enterprise design.

The final architecture introduces additional Headquarters Layer 3 routing paths, backup Branch WAN connectivity, secondary Internet connectivity, and redundant IPv4 and IPv6 routing paths.

HQ-RTR02 is introduced as the secondary Headquarters edge router and is integrated with the Headquarters multilayer switches, both Branch routers, and ISP-RTR01.

A dedicated Linux management workstation is included in the Management VLAN to provide centralized SSH-based administrative access and verification of enterprise network devices.