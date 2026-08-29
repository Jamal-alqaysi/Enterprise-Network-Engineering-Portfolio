
## Overview

During the final enterprise network integration, a small number of configuration and management connectivity issues were encountered and resolved.

Only issues that occurred during the actual implementation of Project 11 are documented in this section. Planned verification activities, including WAN failover, Layer 3 path failover, OSPF route convergence, and NAT/PAT backup-path testing, are documented separately in the Verification section and are not considered troubleshooting incidents.

---

## Issue 1 – OSPF Adjacencies Lost After Passive Interface Configuration

### Problem

During OSPF configuration, existing neighbor adjacencies were unexpectedly lost after applying the passive interface configuration.

OSPF neighbors that had previously reached the FULL state transitioned to the DOWN state.

### Cause

The `passive-interface default` configuration prevented OSPF Hello packets from being transmitted on routed interfaces that were required to establish neighbor relationships.

As a result, OSPF adjacencies could not remain active across those links.

### Resolution

The OSPF passive interface configuration was reviewed, and the required routed interfaces were explicitly configured as non-passive.

Only interfaces that should not establish OSPF neighbor relationships remained passive.

The OSPF neighbor table was then checked again to confirm adjacency restoration.

### Result

- Required OSPF neighbor relationships returned to the FULL state.
- Routing adjacencies across the required redundant Layer 3 paths were restored.
- Passive interfaces remained enabled where OSPF neighbor formation was not required.
- The required OSPF neighbor relationships remained active after the configuration was corrected.

---

## Issue 2 – Linux Management Workstation IPv4 Connectivity

### Problem

The dedicated `linux-mgmt01` management workstation initially had IPv6 connectivity but did not have the required IPv4 connectivity to the Management VLAN.

An SSH connection attempt to HQ-MLS01 at `192.168.99.1` failed with:

```text
Network is unreachable
```

### Cause

The Linux management workstation did not have the required IPv4 address and default gateway configuration for the `192.168.99.0/24` Management network.

Without a valid IPv4 configuration, the workstation could not reach the IPv4 management addresses of the network devices.

### Resolution

The Linux management workstation was configured with the following IPv4 settings:

- IPv4 address: `192.168.99.10/24`
- Default gateway: `192.168.99.254`

The IPv4 configuration was applied to the existing NetworkManager connection to ensure that the settings remained persistent.

Connectivity to the Management VLAN was then tested again before establishing a new SSH session.

### Result

- `linux-mgmt01` successfully established IPv4 connectivity to the Management VLAN.
- The Management VLAN gateway became reachable.
- SSH access to HQ-MLS01 at `192.168.99.1` succeeded.
- The workstation could be used for SSH-based network administration through the Management VLAN.
- The IPv4 management configuration remained persistent after being applied through NetworkManager.

---

## Troubleshooting Summary

The issues encountered during Project 11 were limited and were resolved without modifying the overall enterprise architecture.

The OSPF adjacency issue demonstrated the importance of correctly identifying interfaces that must remain active for dynamic routing when using passive interface policies. After correcting the passive interface configuration, the required OSPF neighbor relationships returned to the FULL state.

The Linux management workstation issue demonstrated the importance of validating both IPv4 and IPv6 management connectivity in a dual-stack environment. After configuring persistent IPv4 addressing and the appropriate default gateway, SSH access to HQ-MLS01 through VLAN 99 was successfully established.

Both identified implementation issues were resolved, and the affected OSPF adjacency and management connectivity functions were successfully restored and verified.