
```
enable
configure terminal

interface Ethernet0/2
 description Backup-Link-to-HQ-RTR02
 ip address 10.0.0.18 255.255.255.252
 ip ospf cost 100
 ipv6 address 2001:DB8:103::2/64
 ipv6 ospf 1 area 0
 ipv6 ospf cost 100
 no shutdown
 exit

router ospf 1
 network 10.0.0.16 0.0.0.3 area 0
 exit

end

copy running-config startup-config
```
