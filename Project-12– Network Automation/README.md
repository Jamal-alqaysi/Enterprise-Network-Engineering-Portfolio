# Project 12 – Network Automation


![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Platform](https://img.shields.io/badge/Platform-EVE--NG-blue)
![Cisco](https://img.shields.io/badge/Vendor-Cisco-1BA0D7)
![Linux](https://img.shields.io/badge/OS-Linux-FCC624)
![Python](https://img.shields.io/badge/Language-Python_3-3776AB)
![Netmiko](https://img.shields.io/badge/Automation-Netmiko-28A745)

## Project Information

| Item     | Value                           |
| -------- | ------------------------------- |
| Project  | Project 12 – Network Automation |
| Version  | v12.0                           |
| Status   | Completed                       |
| Platform | EVE-NG                          |
| Vendor   | Cisco                           |

---

## Overview

Project 12 introduces basic network automation to NorthStar using Python and Netmiko. It automates SSH connections and read-only Cisco IOS verification on two devices without changing the existing network.

---
## Objectives

- Automate SSH-based Cisco IOS show commands.
- Retrieve and analyze interface information.
- Execute commands on two devices using Python loops.
- Handle errors and close SSH sessions safely.

---
## Technologies Used

Python 3 · Netmiko · SSH · Cisco IOS · EVE-NG · Linux

**Devices:** linux-mgmt01, HQ-MLS01, HQ-RTR01

---

## Project Structure

```text
Project-12-Network-Automation/
├── 01-Requirements/
├── 02-Network Design Specification/
├── 03-Implementation/
├── 04-Verification/
├── 05-Troubleshooting/
├── 06-Lessons-Learned/
├── Assets/
├── Configurations/
│   └── project12.py
├── Screenshots/
└── README.md
```

---

## Network Automation Topology

![Network Automation Topology](Assets/P12-Network-Automation-Topology.png)
The diagram shows logical SSH connections from `linux-mgmt01` to **HQ-MLS01 (192.168.99.1)** and **HQ-RTR01 (10.0.0.9)**.

---
## Verification Performed

- SSH and command execution verified on both devices.
- Interface output collected with `show ip interface brief`.
- Basic protocol-state analysis performed.
- `try/except/finally` added for error handling and session cleanup.
- A Netmiko prompt-detection issue was addressed using `send_command_timing()`.

Evidence is retained in **Screenshots**.

---
## Skills Demonstrated

Python · Netmiko · SSH · Cisco IOS · Multi-Device Automation · Troubleshooting

---
## Result

The script retrieved interface information from both devices without modifying network configurations. Final evidence and documentation review remain in progress.

---
## Author

**Jamal Al Qaysi**  
Enterprise Network Engineering Portfolio
