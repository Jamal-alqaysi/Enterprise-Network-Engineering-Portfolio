
## Overview

During the implementation and verification of Project 01, the network infrastructure operated as expected and end-to-end Layer 2 connectivity was successfully established.

One limitation was encountered while attempting to verify SSH remote access from the VPCS end devices used in the EVE-NG environment.

---

## Issue 1 – VPCS SSH Client Limitation

### Problem

SSH remote management was configured on HQ-MLS01.

During verification, an attempt was made to initiate an SSH connection from a VPCS workstation. However, VPCS does not provide a full SSH client capable of establishing remote administrative sessions to Cisco network devices.

As a result, SSH connectivity could not be directly tested from the VPCS workstation.

---

### Cause

The issue was caused by a functional limitation of VPCS rather than an error in the Cisco IOS SSH configuration.

VPCS is designed primarily for lightweight network connectivity testing and does not provide the same remote management capabilities as a full operating system.

---

### Resolution

The SSH configuration on HQ-MLS01 was validated directly through the Cisco IOS configuration.

The following items were verified:

- SSH remote management was enabled.
- Local user authentication was configured.
- VTY lines used local authentication.
- VTY access was restricted to SSH.
- Telnet access was not permitted.

A dedicated Linux management workstation is introduced later in the NorthStar Enterprise Network to provide full SSH client functionality for remote network administration.

---

## Troubleshooting Summary

The only significant limitation encountered during Project 01 was the inability to initiate an SSH session from the VPCS end devices.

This limitation was related to the capabilities of VPCS within the EVE-NG environment and did not indicate a network configuration failure.

The underlying network infrastructure, IPv4 connectivity, and SSH configuration remained operational.