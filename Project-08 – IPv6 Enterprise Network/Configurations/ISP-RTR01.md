
```
ipv6 unicast-routing

interface Ethernet0/0
 ipv6 address 2001:DB8:102::2/64
 ipv6 ospf 1 area 0

ipv6 router ospf 1
 router-id 6.6.6.6
```