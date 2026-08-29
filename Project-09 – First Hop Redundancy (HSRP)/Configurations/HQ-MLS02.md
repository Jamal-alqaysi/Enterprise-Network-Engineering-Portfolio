
```
enable
configure terminal

ip routing

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

interface Vlan10
 description HR
 ip address 192.168.10.2 255.255.255.0
 standby version 2
 standby 10 ip 192.168.10.254
 standby 10 priority 100
 standby 10 preempt
 standby 10 name HR-HSRP
 no shutdown
 exit

interface Vlan20
 description FINANCE
 ip address 192.168.20.2 255.255.255.0
 standby version 2
 standby 20 ip 192.168.20.254
 standby 20 priority 100
 standby 20 preempt
 standby 20 name FINANCE-HSRP
 no shutdown
 exit

interface Vlan30
 description IT
 ip address 192.168.30.2 255.255.255.0
 standby version 2
 standby 30 ip 192.168.30.254
 standby 30 priority 100
 standby 30 preempt
 standby 30 name IT-HSRP
 no shutdown
 exit

interface Vlan99
 description MANAGEMENT
 ip address 192.168.99.2 255.255.255.0
 standby version 2
 standby 99 ip 192.168.99.254
 standby 99 priority 100
 standby 99 preempt
 standby 99 name MGMT-HSRP
 no shutdown
 exit

end

copy running-config startup-config
```