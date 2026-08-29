
## Objective

Extend the existing enterprise network by introducing IPv6 connectivity while preserving all IPv4 services implemented in previous projects.

The project adopts a dual-stack architecture, allowing IPv4 and IPv6 to operate simultaneously across the enterprise network without affecting existing services.

---

## Requirements

- Preserve the existing enterprise topology.
- Preserve the IPv4 addressing plan.
- Preserve all VLANs configured in previous projects.
- Preserve Inter-VLAN Routing.
- Preserve OSPFv2 for IPv4.
- Preserve DHCP services.
- Preserve NAT/PAT operation.
- Preserve ACL security policies.
- Preserve EtherChannel and Rapid PVST+.
- Implement IPv6 addressing across the enterprise network.
- Configure dual-stack operation on all Layer 3 devices.
- Deploy OSPFv3 for IPv6 dynamic routing.
- Verify IPv6 connectivity between Headquarters and branch offices.
- Verify dual-stack operation throughout the enterprise network.

---

## Expected Outcome

At the end of this project, the enterprise network will support both IPv4 and IPv6 simultaneously.

IPv4 services implemented in Projects 01 through 07 will continue to operate without modification, while IPv6 connectivity will be available across all enterprise locations through OSPFv3 dynamic routing.