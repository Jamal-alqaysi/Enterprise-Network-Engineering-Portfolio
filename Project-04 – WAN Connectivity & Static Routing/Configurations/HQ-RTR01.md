```
enable
configure terminal

hostname HQ-RTR01

no ip domain lookup
service password-encryption

enable secret <ENABLE_SECRET>

banner motd #
Unauthorized access is prohibited.
#

username admin privilege 15 secret <ADMIN_SECRET>

line console 0
 password <CONSOLE_PASSWORD>
 login
 logging synchronous
 exec-timeout 10 0
 exit

ip domain name northstar.local

crypto key generate rsa modulus 2048

ip ssh version 2

line vty 0 4
 login local
 transport input ssh
 exec-timeout 10 0
 exit

no ip http server
no ip http secure-server

interface Ethernet0/0
 description WAN to BR1-RTR01
 ip address 10.0.0.1 255.255.255.252
 no shutdown

interface Ethernet0/1
 description Transit to HQ-MLS01
 ip address 10.0.0.9 255.255.255.252
 no shutdown

interface Ethernet0/2
 description Reserved Link to HQ-MLS02
 no ip address
 shutdown

interface Ethernet0/3
 description WAN to BR2-RTR01
 ip address 10.0.0.5 255.255.255.252
 no shutdown

ip route 192.168.10.0 255.255.255.0 10.0.0.10
ip route 192.168.20.0 255.255.255.0 10.0.0.10
ip route 192.168.30.0 255.255.255.0 10.0.0.10
ip route 192.168.99.0 255.255.255.0 10.0.0.10
ip route 192.168.40.0 255.255.255.0 10.0.0.2
ip route 192.168.50.0 255.255.255.0 10.0.0.6

end

copy running-config startup-config
```



