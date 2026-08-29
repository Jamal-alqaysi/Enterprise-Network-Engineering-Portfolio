
```
enable
configure terminal

interface Vlan10
 standby version 2
 standby 10 ip 192.168.10.254
 standby 10 priority 110
 standby 10 preempt
 standby 10 name HR-HSRP
 exit

interface Vlan20
 standby version 2
 standby 20 ip 192.168.20.254
 standby 20 priority 110
 standby 20 preempt
 standby 20 name FINANCE-HSRP
 exit

interface Vlan30
 standby version 2
 standby 30 ip 192.168.30.254
 standby 30 priority 110
 standby 30 preempt
 standby 30 name IT-HSRP
 exit

interface Vlan99
 standby version 2
 standby 99 ip 192.168.99.254
 standby 99 priority 110
 standby 99 preempt
 standby 99 name MGMT-HSRP
 exit

ip dhcp pool HR
 no default-router 192.168.10.1
 default-router 192.168.10.254
 exit

ip dhcp pool FINANCE
 no default-router 192.168.20.1
 default-router 192.168.20.254
 exit

ip dhcp pool IT
 no default-router 192.168.30.1
 default-router 192.168.30.254
 exit

ip dhcp pool MANAGEMENT
 no default-router 192.168.99.1
 default-router 192.168.99.254
 exit

end

copy running-config startup-config
```