
```
enable
configure terminal

hostname HQ-MLS02

no ip domain lookup
ip domain name northstar.local
service password-encryption

enable secret <ENABLE_SECRET>
username admin privilege 15 secret <ADMIN_SECRET>

banner motd ^
Unauthorized access is prohibited.
^

line console 0
 password <CONSOLE_PASSWORD>
 logging synchronous
 login
 exit

crypto key generate rsa modulus 2048
ip ssh version 2

line vty 0 4
 login local
 transport input ssh
 exit

vlan 10
 name HR
 exit

vlan 20
 name FINANCE
 exit

vlan 30
 name IT
 exit

vlan 99
 name MANAGEMENT
 exit

vlan 110
 name HR-VOICE
 exit

vlan 120
 name FINANCE-VOICE
 exit

vlan 130
 name IT-VOICE
 exit

vlan 999
 name NATIVE
 exit

interface range Ethernet0/0 - 2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 switchport trunk allowed vlan 10,20,30,99,110,120,130,999
 no shutdown
 exit

interface Ethernet1/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 switchport trunk allowed vlan 10,20,30,99,110,120,130,999
 no shutdown
 exit

interface Vlan99
 description MANAGEMENT
 ip address 192.168.99.2 255.255.255.0
 no shutdown
 exit

interface Vlan1
 no ip address
 shutdown
 exit

ip default-gateway 192.168.99.1

spanning-tree vlan 10,20,30,99,110,120,130,999 root secondary

end

copy running-config startup-config
```



