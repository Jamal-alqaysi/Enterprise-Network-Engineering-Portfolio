
```
enable
configure terminal

interface Ethernet1/1
 no switchport
 description TRANSIT-TO-HQ-RTR01
 ip address 10.0.0.10 255.255.255.252
 no shutdown
 exit

ip route 192.168.40.0 255.255.255.0 10.0.0.9
ip route 192.168.50.0 255.255.255.0 10.0.0.9

end

copy running-config startup-config
```




