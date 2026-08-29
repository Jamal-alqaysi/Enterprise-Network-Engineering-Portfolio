
## Overview

The implementation was verified to confirm that Inter-VLAN Routing operates successfully across the existing enterprise infrastructure.

The verification process confirms SVI operation, Layer 3 routing, VLAN availability, Inter-VLAN connectivity, ARP learning, and continued IEEE 802.1Q trunk operation.

---

## Verification 1 – Enterprise Topology

The Project 03 topology was verified in EVE-NG after implementing Inter-VLAN Routing on HQ-MLS01.

**Result**

- The existing physical topology remained unchanged.
- Two multilayer switches remained operational.
- Three access switches remained operational.
- Six end-user PCs and six Cisco IP Phones remained connected.
- Layer 3 routing was successfully introduced on HQ-MLS01.

![Figure 2. Project 03 EVE-NG Lab Topology](../Assets/Figure%202.%20Project%2003%20EVE-NG%20Lab%20Topology.png)

---

## Verification 2 – SVI Status

The Switch Virtual Interfaces on HQ-MLS01 were verified to confirm that the departmental gateways were operational.

**Command**

```cisco
show ip interface brief
```

**Result**

- VLAN 10 SVI was operational at `192.168.10.1`.
- VLAN 20 SVI was operational at `192.168.20.1`.
- VLAN 30 SVI was operational at `192.168.30.1`.
- Management VLAN 99 remained operational at `192.168.99.1`.
- All required SVIs were in the `up/up` state.

![SC-01 - SVI Status Verification](../Screenshots/SC-01%20-%20SVI%20Status%20Verification.png)

---

## Verification 3 – Routing Table

The IPv4 routing table on HQ-MLS01 was verified to confirm that the departmental networks were directly connected.

**Command**

```cisco
show ip route
```

**Result**

The routing table contained connected routes for:

- `192.168.10.0/24` through VLAN 10
- `192.168.20.0/24` through VLAN 20
- `192.168.30.0/24` through VLAN 30
- `192.168.99.0/24` through VLAN 99

No gateway of last resort was configured in Project 03.

![SC-02 - Routing Table Verification](../Screenshots/SC-02%20-%20Routing%20Table%20Verification.png)

---

## Verification 4 – VLAN Structure

The existing VLAN structure was verified after enabling Layer 3 routing.

**Command**

```cisco
show vlan brief
```

**Result**

- Departmental Data VLANs remained present.
- Voice VLANs remained present.
- Management VLAN 99 remained present.
- Native VLAN 999 remained present.
- The existing Project 02 VLAN structure was preserved.

![SC-03 - VLAN Verification](../Screenshots/SC-03%20-%20VLAN%20Verification.png)

---

## Verification 5 – Inter-VLAN Connectivity

Inter-VLAN communication was verified from HR-PC01 to devices located in the Finance and IT VLANs.

**Commands**

```text
ping 192.168.20.11
ping 192.168.30.11
```

**Result**

- HR-PC01 successfully reached FIN-PC01 at `192.168.20.11`.
- HR-PC01 successfully reached IT-PC01 at `192.168.30.11`.
- ICMP responses were successfully received for all transmitted packets.
- Inter-VLAN Routing through HQ-MLS01 was operational.

![SC-04 - Inter-VLAN Routing Verification](../Screenshots/SC-04%20-%20Inter-VLAN%20Routing%20Verification.png)

---

## Verification 6 – ARP Table

The ARP table on HQ-MLS01 was verified after successful network communication.

**Command**

```cisco
show ip arp
```

**Result**

- Dynamic IP-to-MAC address mappings were successfully learned.
- ARP entries confirmed Layer 3 communication with connected end devices.

![SC-05 - ARP Table Verification](../Screenshots/SC-05%20-%20ARP%20Table%20Verification.png)

---

## Verification 7 – IEEE 802.1Q Trunks

The existing trunk infrastructure was verified to confirm that Layer 2 transport remained operational after enabling Inter-VLAN Routing.

**Command**

```cisco
show interfaces trunk
```

**Result**

- Inter-switch trunk links remained operational.
- Native VLAN 999 remained configured.
- Required VLANs continued to traverse the trunk infrastructure.
- Project 03 Layer 3 changes did not disrupt the existing trunk configuration.

![SC-06 - Trunk Verification](../Screenshots/SC-06%20-%20Trunk%20Verification.png)

---

## Verification Summary

The verification process confirmed that Inter-VLAN Routing was successfully implemented on HQ-MLS01.

The departmental SVIs were operational, the corresponding networks appeared as directly connected routes, and successful communication was verified between HR, Finance, and IT devices.

The existing VLAN and IEEE 802.1Q trunk infrastructure remained operational after the introduction of Layer 3 routing.