

```
enable
configure terminal

interface range Ethernet0/1 - 2
 switchport port-security
 switchport port-security maximum 1
 switchport port-security mac-address sticky
 switchport port-security violation restrict

ip dhcp snooping
ip dhcp snooping vlan 10,20,30,99
no ip dhcp snooping information option

interface Ethernet0/0
 ip dhcp snooping trust

interface Ethernet0/3
 ip dhcp snooping trust

interface range Ethernet0/1 - 2
 spanning-tree portfast
 spanning-tree bpduguard enable
```

