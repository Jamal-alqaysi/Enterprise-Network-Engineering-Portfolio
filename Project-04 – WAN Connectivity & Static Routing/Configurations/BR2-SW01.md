```
enable
configure terminal

hostname BR2-SW01

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

vlan 50
 name BR2-DATA

vlan 150
 name BR2-VOICE

interface Ethernet0/0
 description LAN Link to BR2-RTR01
 switchport mode access
 switchport access vlan 50
 no shutdown

interface Ethernet0/1
 description BR2-IPPhone01 and BR2-PC01
 switchport mode access
 switchport access vlan 50
 switchport voice vlan 150
 spanning-tree portfast
 spanning-tree bpduguard enable
 no shutdown

end

copy running-config startup-config
```


