
## Overview

Project 12 verifies the implementation of Python-based network automation using Netmiko within the NorthStar Enterprise Network.

The verification focuses on SSH connectivity, Cisco IOS command execution, interface status analysis, multi-device automation, and basic error handling.

All automation tasks were performed without modifying the existing enterprise network configurations or services.

---

## Verification Process

### Step 1 – Verify Python and Netmiko Environment

Python 3.8.10 and the Netmiko library were verified on the Linux automation host.

The successful Netmiko import confirmed that the environment was ready for network automation.

**Verification Evidence:**

![[Screenshots/P12-01-Python-Netmiko-Verification.png]]

---

### Step 2 – Verify Device Connection Parameters

The Python script was configured with the required Cisco device connection parameters, including device type, IP address, and SSH username.

The `getpass()` function was implemented to request SSH passwords securely without storing them directly in the script.

**Verification Evidence:**

![[Screenshots/P12-02-Device-Connection-Parameters.png]]

---

### Step 3 – Verify SSH Connectivity

Netmiko successfully established an SSH connection from the Linux automation host to HQ-MLS01.

The `is_alive()` method confirmed that the SSH session was active.

**Verification Evidence:**

![[Screenshots/P12-03-SSH-Connection-Verification.png]]

---

### Step 4 – Verify Cisco IOS Command Execution

The automation script successfully executed the `show version` command on HQ-MLS01 using Netmiko.

The retrieved output confirmed successful remote command execution and access to device operational information.

**Verification Evidence:**

![[Screenshots/P12-04A-Command-Execution.png]]

![[Screenshots/P12-04B-Command-Output.png]]

---

### Step 5 – Verify Interface Information Retrieval

The `show ip interface brief` command was executed through Netmiko to retrieve interface information from HQ-MLS01.

The output displayed interface names, IP addresses, interface status, and protocol status.

**Verification Evidence:**

![[Screenshots/P12-05-Interface-Verification.png]]

---

### Step 6 – Verify Interface Status Analysis

Python string-processing functions, including `splitlines()` and `split()`, were used to analyze the retrieved interface information.

Conditional statements successfully identified interfaces with a `down` protocol status.

The test identified Vlan1 as having a down protocol status during verification.

**Verification Evidence:**

![[Screenshots/P12-06-Down-Interface-Detection.png]]

![[Screenshots/P12-07-Interface-Analysis-Script.png]]

---

### Step 7 – Verify Multi-Device Automation

The automation script was extended to support multiple Cisco network devices using Python lists, dictionaries, and loops.

Netmiko successfully established SSH connections and executed `show ip interface brief` on both target devices:

- **HQ-MLS01:** 192.168.99.1
- **HQ-RTR01:** 10.0.0.9


The script processed both devices sequentially and retrieved their interface information.

**Verification Evidence:**

![[Screenshots/P12-08-Multi-Device-Script.png]]

![[Screenshots/P12-09-Multi-Device-Verification.png]]

---

### Step 8 – Verify Error Handling and Final Automation

Basic exception handling was implemented using `try`, `except`, and `finally` to handle automation errors and manage SSH session cleanup.

An initial Netmiko prompt detection error occurred during command execution on HQ-RTR01.

The issue was resolved by replacing `send_command()` with `send_command_timing()`.

The final script was executed successfully, retrieving interface information from both HQ-MLS01 and HQ-RTR01 without further reported execution errors.

**Verification Evidence:**

**HQ-MLS01 – Final Verification**

![[Screenshots/P12-10A-HQ-MLS01-Verification.png]]

**HQ-RTR01 – Final Verification**

![[Screenshots/P12-10B-HQ-RTR01-Verification.png]]

**Final Python Automation Script**

![[Screenshots/P12-11-Final-Netmiko-Automation-Script.png]]

---

## Final Verification Result

Project 12 successfully demonstrated basic network automation using Python and Netmiko.

The implementation verified secure SSH connectivity, remote Cisco IOS command execution, interface information retrieval, basic interface status analysis, sequential multi-device automation, and exception handling.

All final automation tests were completed on the selected NorthStar network devices without modifying the existing enterprise network configurations.

**Project 12 – Network Automation: Verification Successful.**