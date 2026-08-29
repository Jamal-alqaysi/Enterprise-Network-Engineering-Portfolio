

## Overview

During the implementation of Project 02, a configuration loss occurred after the EVE-NG lab was recreated.

The issue required the Layer 2 configuration to be rebuilt from the established baseline and resulted in the adoption of a more reliable configuration backup procedure for subsequent projects.

---

## Issue 1 – Configuration Loss After Lab Recreation

### Problem

The initial switch configurations were lost after recreating the EVE-NG lab environment.

As a result, the completed Layer 2 configuration was no longer available on the network devices.

---

### Cause

The device startup configurations had not been exported before the lab topology was recreated.

Without an external configuration backup, the previous device configurations could not be restored directly.

---

### Resolution

The network devices were reconfigured using the established Project 01 baseline and the Project 02 implementation requirements.

The Layer 2 configuration was rebuilt and verified step by step before continuing with the project.

After the rebuild was completed, the **Export all CFGs** procedure in EVE-NG was adopted after major implementation phases to maintain external configuration backups.

---

## Troubleshooting Summary

The configuration loss was successfully resolved by rebuilding the Project 02 Layer 2 implementation from the established baseline.

The incident demonstrated the importance of maintaining external configuration backups when working with virtual network laboratories.

A repeatable configuration export procedure was adopted to reduce the risk of configuration loss during subsequent NorthStar projects.