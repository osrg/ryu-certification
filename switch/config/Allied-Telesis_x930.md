---
layout: default
title: Ryu Certification - Allied Telesis_x930 - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* Allied Telesis x930

# OpenFlow related configuration
<pre>
x930#show running-config
!
service password-encryption
!
hostname x930
!
no banner motd
!
username manager privilege 15 password 8 $1$bJoVec4D$JwOJGPr7YqoExA0GVasdE0
!
no service ssh
!
platform hwfilter-size ipv4-full-ipv6
!
service telnet
!
service http
!
no clock timezone
!
snmp-server
!
!
aaa authentication enable default local
aaa authentication login default local
!
!
!
no stack 1 enable
!
ip domain-lookup
!
!
!
no service dhcp-server
!
no ip multicast-routing
!
spanning-tree mode rstp
!
openflow controller tcp 192.168.200.2 6633
openflow version 1.0 1.3
openflow native vlan 4090
service power-inline
no lacp global-passive-mode enable
no spanning-tree rstp enable
!
switch 1 provision x930-52
!
vlan database
 vlan 2-99,4090 state enable
 vlan 100 state enable
!
interface port1.0.1-1.0.3
 openflow
 switchport
 switchport mode access
!
interface port1.0.4-1.0.6
 switchport
 switchport mode access
!
interface port1.0.7-1.0.44
 shutdown
 switchport
 switchport mode access
!
interface port1.0.45-1.0.52
 switchport
 switchport mode access
!
interface vlan1
 ip address 192.168.200.96/24
!
interface vlan2-100,vlan4090
 no ip igmp snooping tcn query solicit
!
line con 0
line vty 0 4
!
end

x930#
</pre>

# Version information
<pre>
x930#show version

AlliedWare Plus (TM) 5.4.6 08/17/16 05:43:12

Build name : x930-5.4.6-1.2.rel
Build date : Wed Aug 17 05:43:14 UTC 2016
Build type : RELEASE

</pre>


