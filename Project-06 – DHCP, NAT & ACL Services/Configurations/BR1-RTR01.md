
```
enable
configure terminal

interface Ethernet0/1
 ip helper-address 10.0.0.10
 ip access-group BR1-LAN-POLICY in
 exit

ip access-list extended BR1-LAN-POLICY
 permit udp any eq bootpc any eq bootps
 permit udp any eq bootps any eq bootpc
 deny ip 192.168.40.0 0.0.0.255 192.168.99.0 0.0.0.255
 deny ip 192.168.40.0 0.0.0.255 192.168.50.0 0.0.0.255
 deny icmp 192.168.40.0 0.0.0.255 host 203.0.113.2 echo
 permit ip 192.168.40.0 0.0.0.255 192.168.10.0 0.0.0.255
 permit ip 192.168.40.0 0.0.0.255 192.168.20.0 0.0.0.255
 permit ip 192.168.40.0 0.0.0.255 192.168.30.0 0.0.0.255
 permit ip 192.168.40.0 0.0.0.255 any
 exit

end

copy running-config startup-config
```

