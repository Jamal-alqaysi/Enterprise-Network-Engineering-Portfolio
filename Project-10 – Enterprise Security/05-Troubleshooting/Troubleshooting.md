
## Overview

During the implementation of Project 10, all planned Layer 2 security features were evaluated within the EVE-NG laboratory environment using Cisco IOL images.

Port Security, Sticky MAC Address Learning, DHCP Snooping, PortFast, and BPDU Guard were successfully implemented. However, two planned security features could not be reliably implemented and validated because of limitations encountered with the Cisco IOL lab environment rather than configuration errors.

---

## Issue 1 – Dynamic ARP Inspection (DAI)

### Problem

Dynamic ARP Inspection (DAI) could not be successfully validated after enabling DHCP Snooping.

Although end devices successfully obtained IPv4 addresses through DHCP, DAI blocked ARP traffic because the DHCP Snooping Binding Table remained empty.

---

### Investigation

The following observations were confirmed during troubleshooting:

- End devices successfully obtained IPv4 addresses through DHCP.
- User connectivity was restored when DAI was disabled.
- The DHCP Snooping Binding Table remained empty after multiple DHCP lease renewals.
- The issue persisted despite verifying trusted interfaces and DHCP Snooping configuration.

---

### Root Cause

The Cisco IOL Layer 2 image used in the EVE-NG environment did not populate the DHCP Snooping Binding Table as expected during the lab implementation.

Since Dynamic ARP Inspection relies on DHCP Snooping binding information for dynamic ARP validation, DAI could not be reliably operated and validated within the current lab environment.

---

### Resolution

Dynamic ARP Inspection was excluded from the final implementation to preserve stable enterprise connectivity.

---

## Issue 2 – Storm Control

### Problem

Storm Control could not be configured on the enterprise access switches.

---

### Investigation

The Storm Control configuration commands were unavailable on the Cisco IOL Layer 2 image used in the laboratory environment.

Attempts to configure the feature returned unsupported command messages.

---

### Root Cause

The Cisco IOL Layer 2 image used in the EVE-NG environment did not provide the required Storm Control functionality.

This was identified as a limitation of the lab platform rather than a configuration issue.

---

### Resolution

Storm Control was excluded from the final implementation while the supported Layer 2 security features remained in the final deployment.

---

## Final Status

The final Layer 2 security implementation consists of:

- Port Security
- Sticky MAC Address Learning
- DHCP Snooping
- PortFast
- BPDU Guard

Dynamic ARP Inspection and Storm Control remain documented as part of the original Project 10 security plan but were excluded from the final configuration because of limitations encountered with the Cisco IOL lab environment.

After the supported Layer 2 security controls were implemented, IPv4 enterprise connectivity was successfully verified between the tested Headquarters and Branch networks.