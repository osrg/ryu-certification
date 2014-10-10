---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ac784e54-3a50-44c6-88a0-6c38938e6728
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ed7d05eb-3d6d-4f35-9dea-3c3ce4ee34da
controller          : [b02a2bc5-cd75-4afc-98f1-fdc0717566ca]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [210c71ed-e47b-48cf-b623-bc5995c303e3, 4cc4d47b-b23a-4044-90fc-faf3ad705c14, 60f35d18-798c-4474-9de0-d62eb3fc4712, 99b832ac-cf83-42c4-a120-b87670b69393]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b02a2bc5-cd75-4afc-98f1-fdc0717566ca
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=662, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 60f35d18-798c-4474-9de0-d62eb3fc4712
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [075f7369-c69c-4dde-8ace-b2118fe93c13]
name                : eth23

_uuid               : 99b832ac-cf83-42c4-a120-b87670b69393
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [21d77fe9-7144-45c9-b433-1a3a5702fbcb]
name                : br0

_uuid               : 210c71ed-e47b-48cf-b623-bc5995c303e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0dd61a1b-c672-415e-bca2-3941cb191a68]
name                : eth21

_uuid               : 4cc4d47b-b23a-4044-90fc-faf3ad705c14
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9226a4bd-acae-4642-87b5-a54491b1668e]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9226a4bd-acae-4642-87b5-a54491b1668e
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3659186540, tx_dropped=0, tx_errors=0, tx_packets=88373840}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 21d77fe9-7144-45c9-b433-1a3a5702fbcb
admin_state         : down
duplex              : full
ifindex             : 230
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 075f7369-c69c-4dde-8ace-b2118fe93c13
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1450099408, tx_dropped=0, tx_errors=0, tx_packets=6693356}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0dd61a1b-c672-415e-bca2-3941cb191a68
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=232204589, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=146261743, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit bd7fe4e925d73dff879a4a1ac19a4365365e0dd7
Author:     Dmitry Krivenok &lt;krivenok.dmitry@gmail.com&gt;
AuthorDate: Fri Oct 10 08:56:22 2014 +0400
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Oct 9 23:15:54 2014 -0700

    configure: Also check for Python 2.x installed as python2.7.
    
    On ArchLinux &quot;python&quot; points to 3.x version and the right
    2.x python binary is &quot;python2.7&quot;.
    
    Signed-off-by: Dmitry V. Krivenok &lt;krivenok.dmitry@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
