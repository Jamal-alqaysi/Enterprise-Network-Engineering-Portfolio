
## Overview

Project 05 introduced dynamic routing by replacing Static Routing with Open Shortest Path First (OSPF) across the NorthStar Enterprise Network.

The implementation demonstrated how participating Layer 3 devices automatically exchange routing information, eliminating the need for manually configured Static Routes while maintaining the existing enterprise topology.

---

## Key Lessons Learned

- Replaced Static Routing with OSPF without modifying the existing network topology.
- Configured OSPF as a single-area routing domain (Area 0).
- Established OSPF neighbor adjacencies between Headquarters and both branch offices.
- Verified dynamic route learning through the OSPF routing tables.
- Validated Link-State Database (LSDB) synchronization across participating routers.
- Confirmed end-to-end enterprise connectivity using dynamically learned routes.

---

## Project Outcome

Project 05 successfully introduced dynamic routing into the NorthStar Enterprise Network.

OSPF now provides automatic route discovery and exchange between the participating Layer 3 devices while preserving the existing enterprise topology and IPv4 addressing plan.