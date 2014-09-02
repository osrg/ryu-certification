---
layout: default
title: Ryu Certification - EdgeCore_AS4600-54T - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* EdgeCore AS4600-54T

# OpenFlow related configuration
<pre>
(DCSS Routing) #show running-config

!Current Configuration:
!
!System Description " Data Center Switch Software AS4600-54T, 48x1Gb, 4x10Gb, 2x40Gb, 2.1.40.10, Linux 2.6.34.6"
!System Software Version "2.1.40.10"
!System Up Time          "28 days 22 hrs 4 mins 19 secs"
!Cut-through mode is configured as disabled
!Additional Packages     DCSS BGP-4,DCSS QOS,DCSS Multicast,DCSS IPv6,DCSS Routing,DCSS Data Center
!Current SNTP Synchronized Time: SNTP Last Attempt Status Is Not Successful
!
network protocol none
network parms 10.24.46.1 255.0.0.0 ************
vlan database
vlan 100,203
exit

configure
sntp client mode unicast
clock timezone 9 minutes 0
passwords min-length 0
line console
serial baudrate 115200
exit

line telnet
exit

line ssh
exit

no spanning-tree
!

interface 0/1
vlan participation include 100,203
exit



interface 0/2
vlan participation include 100,203
exit



interface 0/21
no openflow port-enable
exit



interface 0/49
no auto-negotiate
speed 10G full-duplex
exit



interface 0/50
no auto-negotiate
speed 10G full-duplex
exit



interface 0/51
no auto-negotiate
speed 10G full-duplex
exit



interface 0/52
no auto-negotiate
speed 10G full-duplex
exit


router ospf
exit
ipv6 router ospf
exit
no isdp run
openflow static-ip-mode
openflow static-ip 10.24.46.1
openflow controller 10.24.150.30 6633 tcp
openflow variant openflow10
openflow default-table full-match
openflow version openflow13
openflow enable
exit
</pre>

# Version information
<pre>
(DCSS Routing) #show version

Switch: 1

System Description.............................  Data Center Switch Software AS4600-54T, 48x1Gb, 4x10Gb, 2x40Gb, 2.1.40.10, Linux 2.6.34.6
Machine Type...................................  Data Center Switch Software AS4600-54T, 48x1Gb, 4x10Gb, 2x40Gb
Machine Model.................................. AS4600-54T
Part Number.................................... BCM56540
Maintenance Level.............................. A
Manufacturer................................... 0xbc00
Burned In MAC Address.......................... 70:72:CF:9F:76:1E
Software Version............................... 2.1.40.10
Loader Version................................. 1.0.0.0
Operating System............................... Linux 2.6.34.6
Network Processing Device...................... BCM56540_B0
Additional Packages............................ DCSS BGP-4
                                                DCSS QOS
                                                DCSS Multicast
                                                DCSS IPv6
                                                DCSS Routing
                                                DCSS Data Center
                                                DCSS OpEN API
                                                DCSS Prototype Open API
</pre>

# Modified test scenario for switch restrictions
<pre>
$ rm ryu/tests/switch/of13/meter/02_*.json

# The switch requires 10 seconds for table miss count.
$ perl -i '-pes/^(INTERVAL = )1/${1}10/' ryu/tests/switch/tester.py
</pre>
