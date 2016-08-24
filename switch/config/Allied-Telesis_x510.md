---
layout: default
title: Ryu Certification - Allied Telesis_x510 - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* Allied Telesis x510

# OpenFlow related configuration
<pre>
x510#show running-config
!
service password-encryption
!
hostname x510
!
no banner motd
!
username manager privilege 15 password 8 $1$bJoVec4D$JwOJGPr7YqoExA0GVasdE0
!
ssh server v2only
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
!
!
no ip multicast-routing
!
spanning-tree mode rstp
!
openflow controller tcp 192.168.200.2 6633
openflow version 1.0 1.3
openflow native vlan 4090
no lacp global-passive-mode enable
no spanning-tree rstp enable
!
switch 1 provision x510-52
!
vlan database
 vlan 2-100 state enable
 vlan 4090 state enable
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
interface port1.0.7-1.0.50
 shutdown
 switchport
 switchport mode access
!
interface port1.0.51-1.0.52
 switchport
 switchport mode access
!
interface vlan1
 ip address 192.168.200.98/24
!
interface vlan10
 ip address 192.168.10.10/24
!
line con 0
line vty 0 4
!
end

x510#
</pre>

# Version information
<pre>
x510#show version

AlliedWare Plus (TM) 5.4.6 08/17/16 05:30:04

Build name : x510-5.4.6-1.2.rel
Build date : Wed Aug 17 05:30:16 UTC 2016
Build type : RELEASE

</pre>

