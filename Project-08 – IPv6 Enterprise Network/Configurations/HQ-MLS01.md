
```
ipv6 unicast-routing

interface Vlan10
 ipv6 address 2001:DB8:10::1/64
 ipv6 ospf 1 area 0

interface Vlan20
 ipv6 address 2001:DB8:20::1/64
 ipv6 ospf 1 area 0

interface Vlan30
 ipv6 address 2001:DB8:30::1/64
 ipv6 ospf 1 area 0

interface Vlan99
 ipv6 address 2001:DB8:99::1/64
 ipv6 ospf 1 area 0

interface Ethernet1/1
 ipv6 address 2001:DB8:1::2/64
 ipv6 ospf 1 area 0

ipv6 router ospf 1
 router-id 2.2.2.2
```