
```
enable
configure terminal

interface Ethernet1/1
 description Link to ISP-RTR01
 ip address 203.0.113.1 255.255.255.252
 ip nat outside
 no shutdown
 exit

interface Ethernet0/0
 ip nat inside
 exit

interface Ethernet0/1
 ip nat inside
 exit

interface Ethernet0/3
 ip nat inside
 exit

ip access-list standard NAT_INSIDE
 permit 192.168.10.0 0.0.0.255
 permit 192.168.20.0 0.0.0.255
 permit 192.168.30.0 0.0.0.255
 permit 192.168.40.0 0.0.0.255
 permit 192.168.50.0 0.0.0.255
 exit

ip nat inside source list NAT_INSIDE interface Ethernet1/1 overload

ip route 0.0.0.0 0.0.0.0 203.0.113.2

router ospf 1
 default-information originate
 exit

end

copy running-config startup-config
```