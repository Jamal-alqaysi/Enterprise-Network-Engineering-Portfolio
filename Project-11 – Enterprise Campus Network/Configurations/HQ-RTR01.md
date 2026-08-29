

```
enable
configure terminal

interface Ethernet1/3
 description To-HQ-MLS02
 ip address 10.0.0.29 255.255.255.252
 ip nat inside
 ip ospf cost 100
 ipv6 address 2001:DB8:2::1/64
 ipv6 ospf 1 area 0
 ipv6 ospf cost 100
 no shutdown
 exit

router ospf 1
 network 10.0.0.28 0.0.0.3 area 0
 exit

end

copy running-config startup-config
```