

```
enable
configure terminal

interface Ethernet0/1
 description TO-HQ-RTR02
 ip address 203.0.113.5 255.255.255.252
 ipv6 address 2001:DB8:105::2/64
 ipv6 ospf 1 area 0
 ipv6 ospf cost 100
 no shutdown
 exit

end 

copy running-config startup-config
```



