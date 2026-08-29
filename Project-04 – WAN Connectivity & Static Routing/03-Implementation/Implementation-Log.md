
## Overview

This section describes the implementation methodology used to deploy the enterprise WAN infrastructure introduced in Project 04.

The deployment follows a structured sequence that extends the existing Headquarters network while minimizing configuration dependencies and ensuring successful verification at each stage.

Cisco IOS configuration commands are intentionally omitted from this document and are provided separately in the **Configurations** directory.

---

## Deployment Sequence

### Step 1 – WAN Router Deployment

Deploy the WAN routers for Headquarters, Branch 1, and Branch 2 within the existing enterprise topology.

The Headquarters router serves as the central WAN gateway, while each branch router provides connectivity for its respective remote office.

---

### Step 2 – Physical Connectivity

Connect all WAN and LAN interfaces according to the approved network topology.

This includes:

- Headquarters router to the Headquarters campus.
- Headquarters router to Branch 1.
- Headquarters router to Branch 2.
- Branch routers to their local access switches.
- Branch access switches to the IP phones.
- IP phones to their respective end-user workstations.

---

### Step 3 – Initial Device Configuration

Apply the standard baseline configuration to all newly deployed routers and branch access switches, including device identification, secure management access, and system hardening.

Configure the branch access switch ports to support both data and voice traffic by assigning the appropriate access VLAN and Voice VLAN for the connected IP phone and workstation.

---

### Step 4 – IPv4 Address Assignment

Assign IPv4 addresses to all WAN interfaces and branch LAN interfaces according to the approved IP addressing plan.

The existing Headquarters addressing remains unchanged from Project 03.

---

### Step 5 – Static Routing

Implement Static Routing between Headquarters, Branch 1, and Branch 2 to establish end-to-end communication across the enterprise WAN.

---

### Step 6 – Connectivity Verification

Verify communication between all enterprise sites to ensure that routing operates correctly across the WAN infrastructure.

Successful verification confirms that Headquarters and both branch offices can communicate using the configured Static Routes.

---

## Implementation Summary

The enterprise WAN infrastructure was successfully deployed by introducing dedicated WAN routers and implementing Static Routing between Headquarters and both branch offices.

The branch access switches were also prepared to support both data and voice traffic, ensuring consistency with the enterprise campus design.

The completed implementation establishes WAN connectivity and Static Routing across the NorthStar Enterprise Network.