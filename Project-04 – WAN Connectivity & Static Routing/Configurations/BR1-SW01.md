```
enable
configure terminal

hostname BR1-SW01

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

spanning-tree mode rapid-pvst

no ip http server
no ip http secure-server

vlan 40
 name BR1-DATA

vlan 140
 name BR1-VOICE

interface Ethernet0/0
 description LAN Link to BR1-RTR01
 switchport mode access
 switchport access vlan 40
 no shutdown

interface Ethernet0/1
 description BR1-IPPhone01 and BR1-PC01
 switchport mode access
 switchport access vlan 40
 switchport voice vlan 140
 spanning-tree portfast
 spanning-tree bpduguard enable
 no shutdown

end

copy running-config startup-config
```
