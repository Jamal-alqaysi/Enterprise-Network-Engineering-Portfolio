
```
enable
configure terminal

interface Ethernet0/0
 switchport port-security
 switchport port-security maximum 1
 switchport port-security mac-address sticky
 switchport port-security violation restrict

ip dhcp snooping
ip dhcp snooping vlan 40
no ip dhcp snooping information option

interface Ethernet0/1
 ip dhcp snooping trust

interface Ethernet0/0
 spanning-tree portfast
 spanning-tree bpduguard enable
```
