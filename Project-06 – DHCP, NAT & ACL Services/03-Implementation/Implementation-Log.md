
## Overview

This section describes the implementation methodology used to deploy centralized network services within the existing NorthStar Enterprise Network.

The deployment follows a structured sequence that preserves the OSPF routing environment while introducing centralized DHCP, DHCP Relay, NAT/PAT, Access Control Lists, and simulated Internet connectivity through ISP-RTR01.

Cisco IOS configuration commands are intentionally omitted from this document and are provided separately in the **Configurations** directory.

---

## Deployment Sequence

### Step 1 – ISP Router Deployment

Deploy ISP-RTR01 and connect it directly to HQ-RTR01 according to the approved topology.

ISP-RTR01 represents the external network and provides the destination used to validate Internet connectivity.

---

### Step 2 – Initial ISP Configuration

Apply the standard baseline configuration to ISP-RTR01.

Configure the physical connection toward HQ-RTR01 and create a loopback interface to represent a simulated external Internet resource.

The existing enterprise devices retain the configurations inherited from Project 05.

---

### Step 3 – Public WAN Connectivity

Assign the approved public IPv4 addresses to the connection between HQ-RTR01 and ISP-RTR01.

Verify direct Layer 3 connectivity across the public WAN link before introducing NAT, ACL, or external routing.

---

### Step 4 – External Routing

Configure HQ-RTR01 with a default route toward ISP-RTR01.

Advertise the enterprise default route through the existing OSPF environment so that Headquarters and both branch offices forward external traffic toward HQ-RTR01.

Configure the required return routing on ISP-RTR01 to support communication with the translated enterprise traffic.

---

### Step 5 – DHCP Service Deployment

Configure centralized DHCP services on HQ-MLS01.

Create DHCP pools for the headquarters data VLANs and both branch LANs while preserving the existing gateway addresses and IPv4 addressing plan.

Exclude all infrastructure and reserved addresses from dynamic allocation.

---

### Step 6 – DHCP Relay Deployment

Configure DHCP Relay on the LAN interfaces of BR1-RTR01 and BR2-RTR01.

The branch routers forward client DHCP broadcasts to the centralized DHCP service on HQ-MLS01.

Verify successful dynamic address allocation before applying the branch security ACLs.

---

### Step 7 – NAT/PAT Deployment

Configure HQ-RTR01 as the enterprise NAT boundary.

Identify the enterprise-facing interfaces as NAT inside and the ISP-facing interface as NAT outside.

Configure PAT so authorized internal networks share the public IPv4 address of HQ-RTR01 when accessing the simulated external resource.

---

### Step 8 – Branch ACL Deployment

Configure Extended ACLs on BR1-RTR01 and BR2-RTR01.

Apply each ACL inbound on the corresponding branch LAN interface.

The ACL policy is implemented in the following order:

- Permit required DHCP client traffic.
- Deny access to Management VLAN 99.
- Deny direct communication with the opposite branch LAN.
- Deny ICMP Echo Requests to the ISP router interface.
- Permit access to authorized headquarters networks.
- Permit access to the simulated Internet resource and other authorized external destinations.

The required DHCP traffic is permitted before the remaining branch security policy is evaluated to ensure that branch clients can obtain their IPv4 configuration through DHCP Relay.

---

### Step 9 – Service Verification

Verify all newly introduced services and policies.

The verification process confirms:

- DHCP address allocation at Headquarters.
- DHCP Relay operation at both branches.
- OSPF and default-route operation.
- NAT/PAT translation.
- Successful access to the ISP loopback resource.
- Failed Ping attempts to the ISP infrastructure interface from branch clients.
- Failed access to Management VLAN 99 from branch clients.
- Failed direct communication between Branch 1 and Branch 2.
- Continued access to authorized headquarters networks.

---

### Step 10 – Configuration Preservation

Save the verified configurations on all modified devices after confirming successful service operation and policy enforcement.

---

## Implementation Summary

Centralized enterprise services were integrated into the existing OSPF infrastructure without redesigning the internal network.

HQ-MLS01 provides centralized DHCP services, the branch routers provide DHCP Relay and traffic filtering, HQ-RTR01 provides NAT/PAT and external routing, and ISP-RTR01 represents the simulated Internet environment.

The final implementation provides automated addressing, controlled enterprise access, protected infrastructure, and external connectivity while preserving the routing foundation established in Project 05.