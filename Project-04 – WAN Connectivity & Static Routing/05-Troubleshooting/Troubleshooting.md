
## Overview

This section documents the issue encountered during the implementation of WAN connectivity and Static Routing in Project 04.

The troubleshooting process focused on identifying the cause of a connectivity failure between Headquarters and Branch 2.

---

## Issue 1 – Headquarters to Branch 2 Connectivity Failure

### Problem

After completing the initial WAN configuration, Headquarters was unable to communicate with Branch 2.

Connectivity tests between HQ-RTR01 and BR2-RTR01 failed, preventing end-to-end communication with the Branch 2 LAN.

---

### Symptoms

- Ping from HQ-RTR01 to `10.0.0.6` failed.
- The Branch 2 LAN was unreachable from Headquarters.
- Static Routes appeared to be configured correctly.
- Branch 1 connectivity remained operational.

---

### Root Cause

The WAN IPv4 address `10.0.0.5/30` was mistakenly configured on the wrong interface of HQ-RTR01.

The physical WAN connection to BR2-RTR01 was connected through `Ethernet0/3`, while the IPv4 address had initially been assigned to a different interface.

As a result, HQ-RTR01 could not establish Layer 3 connectivity with BR2-RTR01.

---

### Resolution

The incorrect IPv4 configuration was removed from the wrong interface and reassigned to the correct WAN interface connected to Branch 2.

After correcting the interface assignment:

- WAN connectivity was restored.
- Ping tests completed successfully.
- Static Routing operated as expected.
- End-to-end communication between Headquarters and Branch 2 was restored.

---

## Troubleshooting Summary

The connectivity failure was caused by an incorrect WAN interface assignment rather than a Static Routing configuration error.

Verifying the physical interface mapping and IPv4 addressing identified the root cause and restored connectivity between Headquarters and Branch 2.