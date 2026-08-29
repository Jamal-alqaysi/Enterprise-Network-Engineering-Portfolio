

```
enable
configure terminal

vlan 10
 name HR

vlan 20
 name FINANCE

vlan 30
 name IT

vlan 99
 name MANAGEMENT

vlan 110
 name HR-VOICE

vlan 120
 name FINANCE-VOICE

vlan 130
 name IT-VOICE

vlan 999
 name NATIVE

interface range Ethernet0/1 - 3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 switchport trunk allowed vlan 10,20,30,99,110,120,130,999
 no shutdown

interface Ethernet1/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 switchport trunk allowed vlan 10,20,30,99,110,120,130,999
 no shutdown

interface Vlan99
 description MANAGEMENT
 ip address 192.168.99.1 255.255.255.0
 no shutdown

interface Vlan1
 no ip address
 shutdown

spanning-tree vlan 10,20,30,99,110,120,130,999 root primary

end

copy running-config startup-config
```
