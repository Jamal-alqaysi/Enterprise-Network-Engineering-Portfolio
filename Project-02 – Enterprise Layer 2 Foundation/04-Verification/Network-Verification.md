
## Overview

The implementation was verified to confirm the successful deployment of the Enterprise Layer 2 Foundation introduced in Project 02.

The verification process confirmed the EVE-NG topology, VLAN deployment, IEEE 802.1Q trunk operation, Management VLAN connectivity, Data and Voice access port configuration, and Rapid PVST+ operation.

---

## Verification 1 – Enterprise Topology

The updated enterprise topology was verified in EVE-NG after completing the Project 02 Layer 2 implementation.

**Result**

- Two multilayer switches were successfully deployed.
- Three access switches were operational.
- Six enterprise workstations were connected.
- Six Cisco IP Phones were successfully added.
- Redundant Layer 2 uplinks were operational.

![Figure 2. Project 02 EVE-NG Lab Topology](../Assets/Figure%202.%20Project%2002%20EVE-NG%20Lab%20Topology.png)

---

## Verification 2 – VLAN Deployment

The VLAN configuration was verified to confirm that all required Project 02 VLANs were successfully created.

**Command**

```cisco
show vlan brief
```

**Result**

- Data VLANs 10, 20, and 30 were successfully created.
- Management VLAN 99 was successfully created.
- Voice VLANs 110, 120, and 130 were successfully created.
- Native VLAN 999 was successfully created.

![SC-01 – VLAN Verification](../Screenshots/SC-01%20%E2%80%93%20VLAN%20Verification.png)

---

## Verification 3 – IEEE 802.1Q Trunk Operation

The inter-switch trunk links were verified to confirm correct IEEE 802.1Q operation.

**Command**

```cisco
show interfaces trunk
```

**Result**

- Required inter-switch links were operating as trunk ports.
- VLAN 999 was configured as the Native VLAN.
- Required Data, Voice, and Management VLANs were transported across the trunk infrastructure.

![SC-02 – Trunk Verification](../Screenshots/SC-02%20%E2%80%93%20Trunk%20Verification.png)

---

## Verification 4 – Management VLAN

The management interfaces were verified to confirm migration to the dedicated Management VLAN 99.

**Command**

```cisco
show ip interface brief
```

**Result**

- VLAN 99 was operational.
- Management IPv4 addresses were correctly configured.
- Network device management was migrated from VLAN 1 to VLAN 99.

![SC-03 – Management VLAN Verification](../Screenshots/SC-03%20%E2%80%93%20Management%20VLAN%20Verification.png)

---

## Verification 5 – Data and Voice Access Ports

User-facing interfaces were verified to confirm the correct Data and Voice VLAN assignments.

**Commands**

```cisco
show running-config interface Ethernet0/1
show running-config interface Ethernet0/2
```

**Result**

- Access mode was correctly configured.
- The appropriate departmental Data VLAN was assigned.
- The appropriate departmental Voice VLAN was assigned.
- PortFast was enabled on the verified user-facing interfaces.

![SC-04 – Access Port Verification](../Screenshots/SC-04%20%E2%80%93%20Access%20Port%20Verification.png)

---

## Verification 6 – STP Root Bridge

The Spanning Tree root bridge election was verified.

**Command**

```cisco
show spanning-tree root
```

**Result**

- HQ-MLS01 was successfully elected as the Primary Root Bridge.
- The enterprise switching infrastructure correctly identified HQ-MLS01 as the Root Bridge for the configured VLANs.

### HQ-MLS01

![SC-05A — HQ-MLS01](../Screenshots/SC-05A%20%E2%80%94%20HQ-MLS01.png)

### HQ-SW01

![SC-05B — HQ-SW01](../Screenshots/SC-05B%20%E2%80%94%20HQ-SW01.png)

---

## Verification 7 – Rapid PVST+ Topology

Rapid PVST+ operation was verified across the redundant Layer 2 topology.

**Command**

```cisco
show spanning-tree
```

**Result**

- Rapid PVST+ was operational.
- Root, Designated, and Alternate port roles were successfully established.
- The Layer 2 topology remained loop-free while redundant links remained available.

![SC-06-A – STP Topology Verification](../Screenshots/SC-06-A%20%E2%80%93%20STP%20Topology%20Verification.png)

![SC-06-B – STP Topology Verification](../Screenshots/SC-06-B%20%E2%80%93%20STP%20Topology%20Verification.png)

![SC-06-C – STP Topology Verification](../Screenshots/SC-06-C%20%E2%80%93%20STP%20Topology%20Verification.png)

---

## Verification 8 – Management Connectivity

Connectivity between the network device management interfaces was verified through VLAN 99.

**Commands**

```cisco
ping 192.168.99.2
ping 192.168.99.11
ping 192.168.99.12
ping 192.168.99.13
```

**Result**

- HQ-MLS02 was reachable through VLAN 99.
- HQ-SW01 was reachable through VLAN 99.
- HQ-SW02 was reachable through VLAN 99.
- HQ-SW03 was reachable through VLAN 99.
- Management VLAN connectivity was successfully established across the enterprise switching infrastructure.

![SC-07 – Management Connectivity](../Screenshots/SC-07%20%E2%80%93%20Management%20Connectivity.png)

---

## Verification Summary

The verification process confirms that Project 02 was successfully implemented.

The expanded enterprise topology, VLAN segmentation, IEEE 802.1Q trunking, Management VLAN, Data and Voice access port assignments, and Rapid PVST+ were successfully verified.

The completed Enterprise Layer 2 Foundation provides the switching infrastructure required for Inter-VLAN Routing introduced in Project 03.