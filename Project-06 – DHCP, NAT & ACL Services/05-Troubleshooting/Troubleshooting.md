
## Overview

This section documents the issues encountered during the implementation of Project 06 and the corrective actions taken to successfully deploy the enterprise network services.

---

## Issue 1 – OSPF Default Route Not Advertised

### Problem

Branch routers did not receive a default route for external network connectivity.

### Cause

The static default route configured on HQ-RTR01 was not being advertised into the OSPF domain.

### Resolution

Configured OSPF to originate the default route using:

```cisco
default-information originate
```

### Result

All enterprise routers successfully learned the default route (O*E2) through OSPF.

---

## Issue 2 – NAT/PAT Translation Not Working

### Problem

Enterprise clients could not access the simulated Internet resource.

### Cause

NAT inside and outside interfaces were not fully configured.

### Resolution

Assigned the correct interfaces as NAT inside and NAT outside and configured PAT using the public interface.

### Result

Enterprise clients successfully accessed the simulated Internet through HQ-RTR01.

---

## Issue 3 – ACL Policy Not Applied

### Problem

ACL filtering rules did not affect enterprise traffic after the ACL was created.

### Cause

The ACL had been created but was not applied to the branch LAN interface.

### Resolution

Applied the ACL inbound on the branch LAN interface using:

```cisco
ip access-group <ACL_NAME> in
```

### Result

The enterprise security policy was successfully enforced.

---

## Issue 4 – DHCP Relay and ACL Interaction

### Problem

Branch clients initially could not obtain IPv4 addresses from the centralized DHCP server.

### Cause

The DHCP Relay configuration required verification on the branch LAN interfaces.

During validation, the inbound branch security ACL also prevented the initial DHCP client traffic from reaching the DHCP Relay process before the client had received an IPv4 address.

### Resolution

Configured and verified the correct DHCP Relay (`ip helper-address`) on each branch LAN interface.

The branch ACL was temporarily removed during troubleshooting to isolate the issue. After confirming successful DHCP address allocation, the ACL policy was updated to explicitly permit the required DHCP client traffic before the remaining security rules were evaluated.

The ACL was then reapplied inbound on the branch LAN interface.

### Result

Branch clients successfully received IPv4 addresses from the centralized DHCP server located at Headquarters while the branch security ACLs remained active.

---

## Troubleshooting Summary

All implementation issues were successfully resolved through systematic verification of routing, DHCP services, NAT/PAT configuration, and ACL deployment.

Following these corrective actions, all enterprise network services operated as designed and passed final verification.