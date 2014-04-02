---
layout: default
title: Ryu Certification - IBM_RackSwitch-G8264 - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* IBM RackSwitch-G8264

# OpenFlow related configuration
<pre>
RS G8264#show running-config
Current configuration:
!
version "7.8.1"
switch-type "IBM Networking Operating System RackSwitch G8264"
iscli-new
!
system timezone 207
! Asia/Tokyo
!

openflow enable
openflow instance 1
        enable
        dpid 0x64
        controller 1 address 10.24.150.30 Mgt-port
        member 29-30,41-42,53-54
        exit
!
!
no system bootp
no system dhcp
no system default-ip mgt
!
!
interface port 29
        no learning
        flood-blocking
        exit
!
interface port 30
        no learning
        flood-blocking
        exit
!
interface port 41
        no learning
        flood-blocking
        exit
!
interface port 42
        no learning
        flood-blocking
        exit
!
interface port 53
        no learning
        flood-blocking
        exit
!
interface port 54
        no learning
        flood-blocking
        exit
!
!
!
interface port 29
        no spanning-tree mst 0 enable
        exit
!
interface port 30
        no spanning-tree mst 0 enable
        exit
!
interface port 41
        no spanning-tree mst 0 enable
        exit
!
interface port 42
        no spanning-tree mst 0 enable
        exit
!
interface port 53
        no spanning-tree mst 0 enable
        exit
!
interface port 54
        no spanning-tree mst 0 enable
        exit
!
no spanning-tree stg-auto
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
no lldp enable
!
interface port 29
        no lldp admin-status
        exit
!
interface port 30
        no lldp admin-status
        exit
!
interface port 41
        no lldp admin-status
        exit
!
interface port 42
        no lldp admin-status
        exit
!
interface port 53
        no lldp admin-status
        exit
!
interface port 54
        no lldp admin-status
        exit
!
!interface ip 1
!       addr &lt;default&gt;
!       enable
!
interface ip 128
        ip address 10.24.64.1
        enable
        exit
!
ip gateway 4 address ************
ip gateway 4 enable
!
!
!
!
!
!
ntp enable
ntp primary-server ************ MGT
!
!
end
</pre>

# Version information
<pre>
RS G8264#show version brief
Software Version 7.8.1.0 (FLASH image1), active configuration.
</pre>

# Modified test scenario for switch restrictions
<pre>
find ryu/tests/switch/of13/ -name '*.json' -print0 | xargs -0 sed -i 's/\"port\":2/\"port\":54/g';
find ryu/tests/switch/of13/ -name '*.json' -print0 | xargs -0 sed -i 's/output:2/output:54/g';
sed -i 's/\"value\":1/\"value\":53/g' ryu/tests/switch/of13/match/00_IN_PORT.json;
sed -i 's/in_port=1/in_port=53/g' ryu/tests/switch/of13/match/00_IN_PORT.json;
sed -i 's/\"value\":2/\"value\":54/g' ryu/tests/switch/of13/match/00_IN_PORT.json;
sed -i 's/in_port=2/in_port=54/g' ryu/tests/switch/of13/match/00_IN_PORT.json;
sed -i 's/TARGET_SENDER_PORT = 2/TARGET_SENDER_PORT = 54/g' ryu/tests/switch/tester.py;
sed -i 's/TARGET_RECEIVE_PORT = 1/TARGET_RECEIVE_PORT = 53/g' ryu/tests/switch/tester.py;
sed -i 's/TESTER_SENDER_PORT = 1/TESTER_SENDER_PORT = 11/g' ryu/tests/switch/tester.py;
sed -i 's/TESTER_RECEIVE_PORT = 2/TESTER_RECEIVE_PORT = 12/g' ryu/tests/switch/tester.py;
</pre>

