
## Overview

During Project 12, several issues were encountered while developing and testing Python-based network automation using Netmiko.

The troubleshooting process focused on resolving Python syntax errors and Netmiko command execution issues without modifying the existing enterprise network configurations.

---

## Issue 1 – Python Syntax Errors

During script development, Python reported syntax errors caused by missing parentheses and incorrect punctuation.

**Resolution:**

- Corrected the affected Python statements.
- Reviewed code indentation and syntax
- Verified the script using `python3 -m py_compile`.

**Result:** The script passed Python syntax verification.

---

## Issue 2 – Netmiko Command Output Detection Failure

During multi-device automation, Netmiko successfully established an SSH connection to HQ-RTR01 but encountered a prompt pattern detection error while executing `show ip interface brief`.

**Resolution:**

- Replaced `send_command()` with `send_command_timing()`.
- Re-executed the automation script on both network devices.

**Result:** Interface information was successfully retrieved from HQ-MLS01 and HQ-RTR01.

---

## Issue 3 – Python Compatibility Warning

A `CryptographyDeprecationWarning` was displayed because the installed Python 3.8 environment is no longer supported by newer versions of the Cryptography library.

**Assessment:**

The warning did not prevent Netmiko imports, SSH connectivity, or successful command execution during the project.

**Result:** Automation remained functional in the existing lab environment. Updating Python is recommended for future compatibility.

---

## Final Troubleshooting Result

The identified Python syntax and Netmiko command execution issues were resolved.

The final automation script successfully connected to both target devices, executed Cisco IOS verification commands, and retrieved operational information.

No changes to the existing enterprise network configurations were required.