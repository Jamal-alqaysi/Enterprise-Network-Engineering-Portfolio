

```
enable
configure terminal

hostname HQ-RTR02

no ip domain lookup
ip domain name northstar.local
service password-encryption
enable secret <ENABLE_SECRET>
username admin privilege 15 secret <ADMIN_SECRET>
ipv6 unicast-routing

banner motd ^
Unauthorized access is prohibited.
^

line console 0
 password <CONSOLE_PASSWORD>
 logging synchronous
 login
 exit

line vty 0 4
 login local
 transport input ssh
 exit

interface Ethernet0/0
 description Routed-Uplink-to-HQ-MLS02
 ip address 10.0.0.13 255.255.255.252
 ip nat inside
 ipv6 address 2001:DB8:3::1/64
 ipv6 ospf 1 area 0
 no shutdown
 exit

interface Ethernet0/1
 description Backup-Link-to-BR1-RTR01
 ip address 10.0.0.17 255.255.255.252
 ip nat inside
 ip ospf cost 100
 ipv6 address 2001:DB8:103::1/64
 ipv6 ospf 1 area 0
 ipv6 ospf cost 100
 no shutdown
 exit

interface Ethernet0/2
 description TO-HQ-MLS01
 ip address 10.0.0.21 255.255.255.252
 ip nat inside
 ip ospf cost 100
 ipv6 address 2001:DB8:4::1/64
 ipv6 ospf 1 area 0
 ipv6 ospf cost 100
 no shutdown
 exit

interface Ethernet0/3
 description Backup-Link-to-BR2-RTR01
 ip address 10.0.0.25 255.255.255.252
 ip nat inside
 ip ospf cost 100
 ipv6 address 2001:DB8:104::1/64
 ipv6 ospf 1 area 0
 ipv6 ospf cost 100
 no shutdown
 exit

interface Ethernet1/1
 description TO-ISP-RTR01
 ip address 203.0.113.6 255.255.255.252
 ip nat outside
 ipv6 address 2001:DB8:105::1/64
 ipv6 ospf 1 area 0
 no shutdown
 exit

router ospf 1
 network 10.0.0.12 0.0.0.3 area 0
 network 10.0.0.16 0.0.0.3 area 0
 network 10.0.0.20 0.0.0.3 area 0
 network 10.0.0.24 0.0.0.3 area 0
 default-information originate metric 100
 exit

ipv6 router ospf 1
 router-id 7.7.7.7
 exit

ip route 0.0.0.0 0.0.0.0 203.0.113.5

ip access-list standard NAT_INSIDE
 10 permit 192.168.10.0 0.0.0.255
 20 permit 192.168.20.0 0.0.0.255
 30 permit 192.168.30.0 0.0.0.255
 40 permit 192.168.40.0 0.0.0.255
 50 permit 192.168.50.0 0.0.0.255
 exit

ip nat inside source list NAT_INSIDE interface Ethernet1/1 overload

end 

copy running-config startup-config
```