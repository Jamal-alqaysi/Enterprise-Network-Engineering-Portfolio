
## Overview

This section verifies that Wide Area Network (WAN) connectivity and Static Routing have been successfully implemented across the NorthStar Enterprise Network.

The verification process confirms WAN operation, static route installation, router interface status, and end-to-end connectivity between Headquarters and both branch offices.

---

## 1. EVE-NG Lab Deployment Verification

### Objective

Verify that the final Enterprise WAN topology has been successfully deployed in the EVE-NG lab environment.

### Expected Result

The deployed topology includes:

- Headquarters campus network
- Headquarters WAN router
- Two branch routers
- Two branch access switches
- Two branch office LANs
- Hub-and-spoke WAN architecture

### Evidence

![Figure 2. WAN Connectivity & Static Routing Topology](../Assets/Figure%202.%20WAN%20Connectivity%20&%20Static%20Routing%20Topology.png)

---

## 2. Headquarters Routing Table Verification

### Objective

Verify that the Headquarters routing devices correctly identify the connected and remote enterprise networks.

### Verification Command

```cisco
show ip route
```

### Expected Result

The routing tables contain the required:

- Connected Headquarters networks
- Connected transit and WAN networks
- Static routes to Branch 1
- Static routes to Branch 2

### Evidence

![SC-01 – HQ-MLS01 Routing Table](../Screenshots/SC-01%20%E2%80%93%20HQ-MLS01%20Routing%20Table.png)

![SC-02 – HQ-RTR01 Routing Table](../Screenshots/SC-02%20%E2%80%93%20HQ-RTR01%20Routing%20Table.png)

---

## 3. Branch Routing Table Verification

### Objective

Verify that both branch routers contain the required connected networks and Static Routes.

### Verification Command

```cisco
show ip route
```

### Expected Result

Each branch router contains:

- Connected LAN network
- Connected WAN network
- Static routes to the Headquarters networks
- Static route to the opposite branch network

### Evidence

![SC-03 – BR1-RTR01 Routing Table](../Screenshots/SC-03%20%E2%80%93%20BR1-RTR01%20Routing%20Table.png)

![SC-04 – BR2-RTR01 Routing Table](../Screenshots/SC-04%20%E2%80%93%20BR2-RTR01%20Routing%20Table.png)

---

## 4. Branch-to-Branch Connectivity Verification

### Objective

Verify successful communication between Branch 1 and Branch 2 across the enterprise WAN.

### Verification Command

```text
ping 192.168.50.10
ping 192.168.40.10
```

### Expected Result

End-user devices in both branch offices communicate successfully through Headquarters using Static Routing.

### Evidence

![SC-05 – Branch 1 to Branch 2 Connectivity Test](../Screenshots/SC-05%20%E2%80%93%20Branch%201%20to%20Branch%202%20Connectivity%20Test.png)

![SC-06 – Branch 2 to Branch 1 Connectivity Test](../Screenshots/SC-06%20%E2%80%93%20Branch%202%20to%20Branch%201%20Connectivity%20Test.png)

---

## 5. Headquarters-to-Branch Connectivity Verification

### Objective

Verify that Headquarters can communicate successfully with both branch office LANs.

### Verification Command

```text
ping 192.168.40.10
ping 192.168.50.10
```

### Expected Result

Headquarters successfully communicates with both remote branch offices.

### Evidence

![SC-07 – Headquarters to Branch Connectivity Test](../Screenshots/SC-07%20%E2%80%93%20Headquarters%20to%20Branch%20Connectivity%20Test.png)

---

## 6. Router Interface Verification

### Objective

Verify that the required WAN, LAN, and transit interfaces are operational.

### Verification Command

```cisco
show ip interface brief
```

### Expected Result

- Required WAN interfaces are operational.
- Required LAN interfaces are operational.
- The Headquarters transit link is operational.
- Required active interfaces are in the `up/up` state.

### Evidence

![SC-08 – HQ-RTR01 Interface Status](../Screenshots/SC-08%20%E2%80%93%20HQ-RTR01%20Interface%20Status.png)

![SC-09 – BR1-RTR01 Interface Status](../Screenshots/SC-09%20%E2%80%93%20BR1-RTR01%20Interface%20Status.png)

![SC-10 – BR2-RTR01 Interface Status](../Screenshots/SC-10%20%E2%80%93%20BR2-RTR01%20Interface%20Status.png)

---

## Verification Summary

The verification process confirms that WAN connectivity and Static Routing have been successfully implemented across the NorthStar Enterprise Network.

The routing tables contain the required connected and static routes, the required router interfaces are operational, and end-to-end communication between Headquarters and both branch offices operates as designed.