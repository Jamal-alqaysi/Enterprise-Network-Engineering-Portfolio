

```
enable
configure terminal

interface Ethernet0/0
 description TO-HQ-RTR02
 no switchport
 ip address 10.0.0.22 255.255.255.252
 ip ospf cost 100
 ipv6 address 2001:DB8:4::2/64
 ipv6 ospf 1 area 0
 ipv6 ospf cost 100
 no shutdown
 exit

router ospf 1
 passive-interface default
 no passive-interface Ethernet0/0
 no passive-interface Ethernet1/1
 network 10.0.0.20 0.0.0.3 area 0
 exit

end

copy running-config startup-config
```

