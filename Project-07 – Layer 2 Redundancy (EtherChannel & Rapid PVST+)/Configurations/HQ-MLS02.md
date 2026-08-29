
```
enable
configure terminal

interface range Ethernet1/0,Ethernet1/2
 channel-group 1 mode active
 no shutdown
 exit

interface Port-channel1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 switchport trunk allowed vlan 10,20,30,40,50,99,999
 no shutdown
 exit

spanning-tree mode rapid-pvst

spanning-tree vlan 10,20,30,40,50,99,999 root secondary

end

copy running-config startup-config
```
