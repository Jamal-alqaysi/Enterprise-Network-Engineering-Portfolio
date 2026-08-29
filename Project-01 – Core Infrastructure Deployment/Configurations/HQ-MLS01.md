
```
enable
configure terminal

hostname HQ-MLS01

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

interface vlan 1
 ip address 192.168.0.1 255.255.255.0
 no shutdown
 exit

no ip http server
no ip http secure-server

end

copy running-config startup-config
```