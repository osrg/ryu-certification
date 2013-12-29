---
layout: default
title: NEC_PF5220 - config
---

# OpenFlow related configuration
<pre>
#Last modified by operator at Sun Dec 29 13:28:29 2013 with version V5.0.0.1
!
clock timezone JST +9
!
vlan 1
  name "VLAN0001"
!
vlan 2
!
vlan 100
!
vlan 203
!
spanning-tree disable
spanning-tree mode pvst
!
interface gigabitethernet 0/1
  switchport mode trunk
  switchport trunk allowed vlan 100,203
  switchport trunk native vlan 1
!
interface gigabitethernet 0/2
  switchport mode trunk
  switchport trunk allowed vlan 100,203
  switchport trunk native vlan 1
!
interface gigabitethernet 0/3
  switchport mode access
!
interface gigabitethernet 0/4
  switchport mode access
!
interface gigabitethernet 0/5
  switchport mode access
!
interface gigabitethernet 0/6
  switchport mode access
!
interface gigabitethernet 0/7
  switchport mode access
!
interface gigabitethernet 0/8
  switchport mode access
!
interface gigabitethernet 0/9
  switchport mode access
!
interface gigabitethernet 0/10
  switchport mode access
!
interface gigabitethernet 0/11
  switchport mode access
!
interface gigabitethernet 0/12
  switchport mode access
!
interface gigabitethernet 0/13
  switchport mode access
  switchport access vlan 2
!
interface gigabitethernet 0/14
  switchport mode access
!
interface gigabitethernet 0/15
  switchport mode access
!
interface gigabitethernet 0/16
  switchport mode access
!
interface gigabitethernet 0/17
  switchport mode access
!
interface gigabitethernet 0/18
  switchport mode access
!
interface gigabitethernet 0/19
  switchport mode access
!
interface gigabitethernet 0/20
  switchport mode access
!
interface gigabitethernet 0/21
  switchport mode access
!
interface gigabitethernet 0/22
  switchport mode access
!
interface gigabitethernet 0/23
  switchport mode access
!
interface gigabitethernet 0/24
  switchport mode access
!
interface tengigabitethernet 0/25
  switchport mode access
!
interface tengigabitethernet 0/26
  switchport mode access
!
interface vlan 1
!
interface vlan 2
  ip address 10.24.52.1 255.0.0.0
!
line vty 0 2
!
ntp server ************
!
openflow-table-resource mode 11
!
openflow openflow-id 1 real-switch
  protocol-version 04
  controller controller-name cntl1 1 10.24.150.30 port 6633 tcp
  dpid 0000000000005220
  openflow-interface gigabitethernet 0/1-2
  enable
!
</pre>

# Version information
<pre>
# show version software
Date 2013/12/29 13:59:45 JST
S/W: OS-F3SL Ver. V5.0.0.1
</pre>

