

```
enable
configure terminal

interface Ethernet0/3
 description Routed-Uplink-to-HQ-RTR02
 no switchport
 ip address 10.0.0.14 255.255.255.252
 ipv6 address 2001:DB8:3::2/64
 ipv6 ospf 1 area 0
 no shutdown
 exit

interface Ethernet1/3
 description To-HQ-RTR01
 no switchport
 ip address 10.0.0.30 255.255.255.252
 ip ospf cost 100
 ipv6 address 2001:DB8:2::2/64
 ipv6 ospf 1 area 0
 ipv6 ospf cost 100
 no shutdown
 exit

router ospf 1
 passive-interface default
 no passive-interface Ethernet0/3
 no passive-interface Ethernet1/3
 network 10.0.0.12 0.0.0.3 area 0
 network 10.0.0.28 0.0.0.3 area 0
 exit

ipv6 router ospf 1
 passive-interface default
 no passive-interface Ethernet0/3
 no passive-interface Ethernet1/3
 exit

end

copy running-config startup-config
```

