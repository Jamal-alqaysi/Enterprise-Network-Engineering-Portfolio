
```
enable
configure terminal

no ip route 192.168.10.0 255.255.255.0 10.0.0.10
no ip route 192.168.20.0 255.255.255.0 10.0.0.10
no ip route 192.168.30.0 255.255.255.0 10.0.0.10
no ip route 192.168.99.0 255.255.255.0 10.0.0.10
no ip route 192.168.40.0 255.255.255.0 10.0.0.2
no ip route 192.168.50.0 255.255.255.0 10.0.0.6

router ospf 1
 network 10.0.0.0 0.0.0.3 area 0
 network 10.0.0.4 0.0.0.3 area 0
 network 10.0.0.8 0.0.0.3 area 0

end

copy running-config startup-config
```
