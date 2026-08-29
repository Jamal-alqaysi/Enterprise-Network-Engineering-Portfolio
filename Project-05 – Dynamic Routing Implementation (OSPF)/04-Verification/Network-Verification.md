
## Overview

This section verifies that Open Shortest Path First (OSPF) has been successfully implemented across the NorthStar Enterprise Network.

The verification process confirms OSPF neighbor establishment, dynamic route learning, routing table updates, OSPF database population, and end-to-end connectivity between Headquarters and both branch offices.

---

## 1. EVE-NG Lab Deployment Verification

### Objective

Verify that the final Enterprise OSPF topology has been successfully deployed in the EVE-NG lab environment.

### Expected Result

The deployed topology includes:

- Headquarters multilayer switch
- Headquarters WAN router
- Two branch routers
- Two branch access switches
- Headquarters campus network
- Two branch office LANs
- Hub-and-spoke WAN architecture
- OSPF dynamic routing

### Evidence

![Figure 2. Enterprise OSPF Topology](../Assets/Figure%202.%20Enterprise%20OSPF%20Topology.png)

---

## 2. Headquarters OSPF Neighbor Verification

### Objective

Verify that Headquarters has successfully established OSPF neighbor relationships.

### Verification Command

```cisco
show ip ospf neighbor
```

### Expected Result

HQ-RTR01 successfully forms OSPF neighbor adjacencies with:

- HQ-MLS01
- BR1-RTR01
- BR2-RTR01

### Evidence

![SC-01 – HQ-RTR01 OSPF Neighbor Verification](../Screenshots/SC-01%20%E2%80%93%20HQ-RTR01%20OSPF%20Neighbor%20Verification.png)

---

## 3. Branch OSPF Neighbor Verification

### Objective

Verify that each branch router has successfully established an OSPF neighbor relationship with Headquarters.

### Verification Command

```cisco
show ip ospf neighbor
```

### Expected Result

Each branch router establishes one FULL OSPF adjacency with HQ-RTR01.

### Evidence

![SC-06 – BR1-RTR01 OSPF Neighbor Verification](../Screenshots/SC-06%20%E2%80%93%20BR1-RTR01%20OSPF%20Neighbor%20Verification.png)

![SC-08 – BR2-RTR01 OSPF Neighbor Verification](../Screenshots/SC-08%20%E2%80%93%20BR2-RTR01%20OSPF%20Neighbor%20Verification.png)

---

## 4. Dynamic Routing Table Verification

### Objective

Verify that OSPF has successfully learned remote enterprise networks.

### Verification Command

```cisco
show ip route ospf
```

### Expected Result

The routing tables contain dynamically learned routes identified by the **O** route code.

### Evidence

![SC-02 – HQ-RTR01 OSPF Routing Table](../Screenshots/SC-02%20%E2%80%93%20HQ-RTR01%20OSPF%20Routing%20Table.png)

![SC-05 – HQ-MLS01 OSPF Routing Table](../Screenshots/SC-05%20%E2%80%93%20HQ-MLS01%20OSPF%20Routing%20Table.png)

![SC-07 – BR1-RTR01 OSPF Routing Table](../Screenshots/SC-07%20%E2%80%93%20BR1-RTR01%20OSPF%20Routing%20Table.png)

![SC-09 – BR2-RTR01 OSPF Routing Table](../Screenshots/SC-09%20%E2%80%93%20BR2-RTR01%20OSPF%20Routing%20Table.png)

---

## 5. OSPF Database Verification

### Objective

Verify that the OSPF Link-State Database (LSDB) has been successfully populated.

### Verification Command

```cisco
show ip ospf database
```

### Expected Result

The OSPF database contains Link-State Advertisements (LSAs) for the participating OSPF routers.

### Evidence

![SC-03 – HQ-RTR01 OSPF Database](../Screenshots/SC-03%20%E2%80%93%20HQ-RTR01%20OSPF%20Database.png)

---

## 6. End-to-End Connectivity Verification

### Objective

Verify successful communication between Headquarters and both branch offices after replacing Static Routing with OSPF.

### Verification Command

```text
ping 192.168.40.10
ping 192.168.50.10
```

### Expected Result

The required enterprise sites communicate successfully through dynamically learned OSPF routes.

### Evidence

![SC-11 – HQ to Branches OSPF Connectivity](../Screenshots/SC-11%20%E2%80%93%20HQ%20to%20Branches%20OSPF%20Connectivity.png)

![SC-10 – BR1 to BR2 OSPF Connectivity](../Screenshots/SC-10%20%E2%80%93%20BR1%20to%20BR2%20OSPF%20Connectivity.png)

---

## Verification Summary

The verification process confirms that Static Routing has been successfully replaced by OSPF across the NorthStar Enterprise Network.

OSPF neighbor adjacencies, dynamically learned routes, the OSPF Link-State Database, and end-to-end connectivity operate successfully across the existing enterprise WAN.