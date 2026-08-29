
## Overview

Project 09 introduces First Hop Redundancy Protocol (HSRP) into the Headquarters campus to provide default gateway redundancy while preserving the enterprise infrastructure implemented in previous projects.

The implementation enables HQ-MLS02 for Layer 3 operation and configures it to participate as the Standby HSRP gateway. HQ-MLS01 remains the preferred Active gateway.

The Headquarters DHCP gateway configuration is also updated so clients use the HSRP virtual IP addresses as their default gateways.

---

## Implementation Process

### Step 1 – Enable Layer 3 Operation on HQ-MLS02

HQ-MLS02 is enabled for Layer 3 operation to support participation in the HSRP gateway redundancy design.

The required Headquarters VLANs are maintained on HQ-MLS02, and Layer 3 Switch Virtual Interfaces (SVIs) are configured for VLANs 10, 20, 30, and 99.

Each SVI is assigned an individual IPv4 address within its corresponding subnet, allowing HQ-MLS02 to participate as the secondary Layer 3 gateway.

---

### Step 2 – Configure HSRP on HQ-MLS01

HSRP Version 2 is configured on the Headquarters VLAN interfaces of HQ-MLS01.

A dedicated HSRP group and virtual IP address are assigned to each VLAN.

HQ-MLS01 is configured with a priority of 110, making it the preferred Active gateway during normal operation.

Preemption is enabled so HQ-MLS01 can automatically resume the Active role after recovering from a failure.

---

### Step 3 – Configure HSRP on HQ-MLS02

HSRP Version 2 is configured on the corresponding VLAN interfaces of HQ-MLS02.

HQ-MLS02 participates in the same HSRP groups and uses the same virtual gateway addresses as HQ-MLS01.

HQ-MLS02 operates with a priority of 100, allowing it to remain in the Standby state while HQ-MLS01 is available.

Preemption is also enabled as part of the HSRP configuration.

---

### Step 4 – Update DHCP Default Gateways

The Headquarters DHCP configuration is updated to distribute the HSRP virtual IP addresses as the default gateways for the Headquarters VLANs.

The previous physical gateway addresses associated with HQ-MLS01 are replaced in the DHCP pools by the corresponding HSRP virtual gateway addresses.

The resulting virtual gateways are:

| VLAN | HSRP Virtual Gateway |
|------|----------------------|
| 10 | 192.168.10.254 |
| 20 | 192.168.20.254 |
| 30 | 192.168.30.254 |
| 99 | 192.168.99.254 |

This allows DHCP clients to use a consistent logical default gateway regardless of which multilayer switch currently holds the Active HSRP role.

---

### Step 5 – Preserve Existing Enterprise Services

The existing enterprise infrastructure and services implemented in previous projects are preserved while HSRP is introduced.

The HSRP implementation is integrated with the existing network without redesigning the previously deployed routing, switching, security, IPv4, or IPv6 architecture.

The primary supporting modification to an existing service is the DHCP default gateway update required for clients to use the new HSRP virtual addresses.

---

### Step 6 – Validate HSRP Operation

HSRP operation is verified on both Headquarters multilayer switches to confirm the expected Active and Standby roles.

The configured virtual gateway addresses, HSRP priorities, and preemption behavior are verified.

DHCP client information is checked to confirm that clients receive the HSRP virtual gateway address.

Existing enterprise connectivity is also verified after the HSRP implementation.

---

### Step 7 – Validate HSRP Failover and Recovery

HSRP failover is tested on VLAN 10 by simulating the loss of the Active gateway role on HQ-MLS01.

HQ-MLS02 is verified to assume the Active role for VLAN 10 while the HSRP virtual gateway address remains unchanged.

After HQ-MLS01 is restored, HSRP preemption allows it to resume the preferred Active role.

The failover and failback states are verified to confirm successful gateway redundancy operation.