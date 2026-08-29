
## Overview

Project 06 introduced centralized enterprise network services by integrating DHCP, DHCP Relay, NAT/PAT, and Access Control Lists (ACLs) into the existing OSPF-based enterprise network.

The implementation demonstrated how multiple network services can operate together while maintaining scalability, security, and centralized administration.

---

## Key Lessons

- Centralizing DHCP services simplifies IP address management across multiple enterprise sites.
- DHCP Relay enables remote branch networks to obtain IP addresses from a centralized DHCP server without deploying additional servers.
- PAT allows multiple internal devices to share a single public IPv4 address, conserving public address space.
- NAT should be deployed at the enterprise edge router to provide a single controlled point for Internet access.
- Extended ACLs should be placed as close to the traffic source as possible to improve security and reduce unnecessary traffic.
- Proper ACL rule order is essential, as Cisco IOS processes ACL entries sequentially from top to bottom.
- Enterprise security policies can restrict access to sensitive networks while maintaining authorized business communication.
- Verifying each service independently before testing end-to-end connectivity simplifies troubleshooting and reduces deployment time.

---

## Project Outcome

Project 06 successfully transformed the enterprise network from a routed infrastructure into a service-enabled enterprise environment by introducing centralized network services and security controls.

Centralized DHCP, DHCP Relay, NAT/PAT, and Extended ACLs now operate together across the existing OSPF-based enterprise network while maintaining controlled internal and external connectivity.