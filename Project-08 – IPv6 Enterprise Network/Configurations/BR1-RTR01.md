
```
ipv6 unicast-routing

interface Ethernet0/0
 ipv6 address 2001:DB8:100::2/64
 ipv6 ospf 1 area 0

interface Ethernet0/1
 ipv6 address 2001:DB8:40::1/64
 ipv6 ospf 1 area 0

ipv6 router ospf 1
 router-id 4.4.4.4
```