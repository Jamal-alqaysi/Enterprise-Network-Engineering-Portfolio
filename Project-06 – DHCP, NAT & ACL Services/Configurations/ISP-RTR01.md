
```
enable
configure terminal

hostname ISP-RTR01

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
 description Link to HQ-RTR01
 ip address 203.0.113.2 255.255.255.252
 no shutdown
 exit

interface Loopback0
 description Simulated Internet Resource
 ip address 203.0.114.10 255.255.255.255
 exit

end

copy running-config startup-config
```