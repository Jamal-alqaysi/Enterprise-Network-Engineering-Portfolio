
## Overview

The implementation was verified to confirm the successful deployment of the initial NorthStar Enterprise Network infrastructure.

The verification process confirmed that the network devices were operational, IPv4 addressing was correctly configured, SSH management was enabled, and end-to-end Layer 2 connectivity was successfully established across the single-subnet enterprise environment.

---

## Verification 1 – Enterprise Topology

The Project 01 enterprise topology was verified in EVE-NG after deploying the initial network infrastructure.

**Result**

- HQ-MLS01 was successfully deployed as the Distribution Layer multilayer switch.
- HQ-SW01, HQ-SW02, and HQ-SW03 were successfully deployed as Access Layer switches.
- Six enterprise workstations were successfully connected to the access layer.
- All required physical network links were operational.

![Figure 2. Project 01 EVE-NG Lab Topology](../Assets/Figure%202.%20Project%2001%20EVE-NG%20Lab%20Topology.png)

---

## Verification 2 – HQ-MLS01 Interface Status

The interface status of HQ-MLS01 was verified.

**Command**

```cisco
show ip interface brief
```

**Result**

- Required interfaces were operational.
- The HQ-MLS01 management interface was active.
- The configured management IPv4 address was operational.

![SC-01 - HQ-MLS01 Interface Status](../Screenshots/SC-01%20-%20HQ-MLS01%20Interface%20Status.png)

---

## Verification 3 – Access Switch Interface Status

The interface status of the enterprise access switches was verified.

**Command**

```cisco
show ip interface brief
```

**Result**

- Required access switch interfaces were operational.
- Management interfaces were successfully configured.
- HQ-SW01 was reachable at `192.168.0.2`.
- HQ-SW02 was reachable at `192.168.0.3`.
- HQ-SW03 was reachable at `192.168.0.4`.

### HQ-SW01

![SC-03 - HQ-SW01 Interface Status](../Screenshots/SC-03%20-%20HQ-SW01%20Interface%20Status.png)

### HQ-SW02

![SC-04 - HQ-SW02 Interface Status](../Screenshots/SC-04%20-%20HQ-SW02%20Interface%20Status.png)

### HQ-SW03

![SC-05 - HQ-SW03 Interface Status](../Screenshots/SC-05%20-%20HQ-SW03%20Interface%20Status.png)

---

## Verification 4 – End Device IPv4 Configuration

Representative enterprise workstations were verified to confirm correct static IPv4 addressing.

**Command**

```text
show ip
```

**Result**

- HR-PC01 was correctly configured within the `192.168.0.0/24` network.
- FIN-PC01 was correctly configured within the `192.168.0.0/24` network.
- IT-PC01 was correctly configured within the `192.168.0.0/24` network.
- All representative workstations operated within the same IPv4 subnet.

### HR-PC01

![SC-06 - HR-PC01 IP Configuration](../Screenshots/SC-06%20-%20HR-PC01%20IP%20Configuration.png)

### FIN-PC01

![SC-10 - FIN-PC01 IP Configuration](../Screenshots/SC-10%20-%20FIN-PC01%20IP%20Configuration.png)

### IT-PC01

![SC-11 - IT-PC01 IP Configuration](../Screenshots/SC-11%20-%20IT-PC01%20IP%20Configuration.png)

---

## Verification 5 – HQ-MLS01 Management Connectivity

Connectivity between HR-PC01 and the HQ-MLS01 management interface was verified.

**Verification**

- HR-PC01 to HQ-MLS01 (`192.168.0.1`)

**Result**

- HR-PC01 successfully reached the HQ-MLS01 management interface.
- Layer 2 connectivity across the enterprise switching infrastructure was operational.

![SC-07 - HR-PC01 Gateway Connectivity Test](../Screenshots/SC-07%20-%20HR-PC01%20Gateway%20Connectivity%20Test.png)

---

## Verification 6 – End-to-End Enterprise Connectivity

Connectivity between representative enterprise workstations was verified using ICMP Echo Requests.

**Verification**

- HR-PC01 to FIN-PC01
- HR-PC01 to IT-PC01

**Result**

- HR-PC01 successfully reached FIN-PC01.
- HR-PC01 successfully reached IT-PC01.
- End-to-end Layer 2 connectivity across the enterprise network was operational.

### HR-PC01 to FIN-PC01

![SC-08 - HR-PC01 to FIN-PC01 Connectivity Test](../Screenshots/SC-08%20-%20HR-PC01%20to%20FIN-PC01%20Connectivity%20Test.png)

### HR-PC01 to IT-PC01

![SC-09 - HR-PC01 to IT-PC01 Connectivity Test](../Screenshots/SC-09%20-%20HR-PC01%20to%20IT-PC01%20Connectivity%20Test.png)

---

## Verification 7 – SSH Configuration

SSH configuration was verified on HQ-MLS01 to confirm secure remote management capability.

**Command**

```cisco
show running-config | section line vty
```

**Result**

- Local authentication was configured.
- VTY lines were configured for SSH access.
- Telnet access was not permitted.
- Secure remote management was successfully enabled.

![SC-12 - HQ-MLS01 SSH Configuration](../Screenshots/SC-12%20-%20HQ-MLS01%20SSH%20Configuration.png)

---

## Verification Summary

The verification process confirms that Project 01 was successfully implemented.

The initial NorthStar Enterprise Network infrastructure was successfully deployed in EVE-NG. The Distribution Layer and Access Layer switches were operational, enterprise workstations were correctly configured within the `192.168.0.0/24` network, and end-to-end Layer 2 connectivity was successfully verified.

Secure SSH management was also configured and verified on HQ-MLS01, establishing the initial network management foundation for subsequent projects.

The completed infrastructure provides a stable baseline for the enterprise technologies introduced in the following NorthStar projects.