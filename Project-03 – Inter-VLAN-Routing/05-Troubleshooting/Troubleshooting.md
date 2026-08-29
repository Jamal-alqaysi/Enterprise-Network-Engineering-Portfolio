
## Overview

This section documents the implementation issue encountered during Project 03 and the steps used to verify the expected Layer 3 behaviour.

---

## Issue 1 – Layer 3 Routing Verification

### Problem

After enabling Layer 3 routing on HQ-MLS01, the `ip routing` command did not appear in the running configuration as expected.

This initially created uncertainty about whether Layer 3 routing had been successfully enabled.

---

### Cause

The Cisco IOL Layer 3 image used in the EVE-NG environment provides Layer 3 routing functionality by default.

As a result, the `ip routing` command was not displayed in the running configuration even though routing functionality was operational.

---

### Resolution

Rather than relying only on the presence of the `ip routing` command in the running configuration, Layer 3 functionality was verified operationally by confirming:

- Active departmental Switch Virtual Interfaces (SVIs)
- Connected departmental networks in the IPv4 routing table
- Successful Inter-VLAN communication between end-user devices

These verification results confirmed that HQ-MLS01 was successfully performing Layer 3 routing.

---

## Troubleshooting Summary

The absence of the `ip routing` command from the running configuration did not indicate a routing failure.

Layer 3 functionality was successfully confirmed through operational SVIs, connected routes, and successful Inter-VLAN communication.

This demonstrated the importance of validating actual device behavior rather than relying on the presence of a single configuration command.