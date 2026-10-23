## Overview

Project 12 introduces Python-based network automation using Netmiko to simplify device management and operational verification across the NorthStar Enterprise Network.

The implementation focuses on automating SSH connections, Cisco IOS command execution, and operational data collection while preserving the existing enterprise topology, configurations, and services.

---
## Implementation Process

### Step 1 – Prepare the Automation Environment

The `linux-mgmt01` host serves as the centralized automation workstation within the existing EVE-NG lab environment.

Python 3 and Netmiko installation have been verified, and manual SSH connectivity to `HQ-MLS01` has been successfully tested.

The `project12.py` script is prepared for automation development.

---

### Step 2 – Implement Single-Device Automation

A Python automation script will be developed to establish an SSH connection to `HQ-MLS01` using Netmiko.

Device connection parameters will be organized using a Python dictionary, allowing the script to execute Cisco IOS verification commands and retrieve their outputs.

---

### Step 3 – Implement Multi-Device Automation

The automation script will be extended to support multiple Headquarters and Branch network devices.

Python lists, loops, and functions will be used to automate repetitive command execution and collect operational information from selected devices.

---

### Step 4 – Implement Error Handling

Basic exception handling will be introduced to manage SSH connection failures, authentication errors, and device communication issues.

The automation script will provide meaningful error messages and ensure proper SSH session termination.

---

### Step 5 – Verify Network Automation

The automation functionality will be tested to confirm successful SSH connectivity, command execution, and output collection.

The verification process will include:

- SSH connectivity between the automation host and target devices.
- Successful execution of Cisco IOS verification commands.
- Accurate retrieval of device command outputs.
- Multi-device automation functionality.
- Error handling and proper SSH session termination.
- Preservation of existing enterprise network services.