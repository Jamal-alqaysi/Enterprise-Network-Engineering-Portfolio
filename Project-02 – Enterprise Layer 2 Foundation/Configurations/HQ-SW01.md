

```
enable
configure terminal

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

interface range Ethernet0/0 , Ethernet0/3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 switchport trunk allowed vlan 10,20,30,99,110,120,130,999
 no shutdown
 exit

interface Ethernet0/1
 description HR-PC01
 switchport mode access
 switchport access vlan 10
 switchport voice vlan 110
 spanning-tree portfast
 no shutdown
 exit

interface Ethernet0/2
 description FIN-PC01
 switchport mode access
 switchport access vlan 20
 switchport voice vlan 120
 spanning-tree portfast
 no shutdown
 exit

interface Vlan99
 description MANAGEMENT
 ip address 192.168.99.11 255.255.255.0
 no shutdown
 exit

interface Vlan1
 no ip address
 shutdown
 exit

no ip default-gateway 192.168.0.1
ip default-gateway 192.168.99.1

end

copy running-config startup-config
```


