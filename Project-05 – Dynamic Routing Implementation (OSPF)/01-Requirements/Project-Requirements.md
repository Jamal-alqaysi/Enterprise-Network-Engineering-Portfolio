
## Project Objective

Extend the enterprise routing infrastructure by replacing Static Routing with Open Shortest Path First (OSPF), enabling dynamic route exchange between Headquarters and both branch offices.

---
## Functional Requirements

The implementation shall meet the following requirements:

- Preserve the existing enterprise topology implemented in Project 04.
- Remove all previously configured Static Routes.
- Configure OSPF on Headquarters and both branch routers.
- Advertise all Headquarters, Branch, and WAN networks through OSPF.
- Maintain connectivity between Headquarters and both branch offices.
- Maintain connectivity between Branch 1 and Branch 2.
- Preserve the existing Inter-VLAN Routing provided by HQ-MLS01.
- Maintain the existing IPv4 addressing plan.
- Maintain the existing hub-and-spoke WAN architecture.
- Verify successful OSPF neighbor establishment.
- Verify dynamic route learning across the enterprise network.
- Verify end-to-end communication after replacing Static Routing.

---
## Technical Requirements

### Platform

- EVE-NG Community Edition

### Network Devices

- HQ-MLS01
- HQ-RTR01
- BR1-RTR01
- BR2-RTR01
- BR1-SW01
- BR2-SW01

### Routing Protocol

- OSPFv2 (Single Area)

### OSPF Area

- Area 0

### IP Version

- IPv4

---
## Expected Outcome

Upon completion of this project:

- Static Routing is fully replaced by OSPF.
- All participating Layer 3 devices dynamically exchange routing information.
- Headquarters and both branch offices maintain full end-to-end connectivity.
- The enterprise network operates using dynamic IPv4 routing while preserving the existing topology and addressing plan.