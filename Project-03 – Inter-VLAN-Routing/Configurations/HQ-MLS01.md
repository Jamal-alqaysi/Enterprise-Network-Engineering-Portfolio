
```
enable
configure terminal

ip routing

interface Vlan10
 description HR Gateway
 ip address 192.168.10.1 255.255.255.0
 no shutdown

interface Vlan20
 description FINANCE Gateway
 ip address 192.168.20.1 255.255.255.0
 no shutdown

interface Vlan30
 description IT Gateway
 ip address 192.168.30.1 255.255.255.0
 no shutdown

end

copy running-config startup-config
```




