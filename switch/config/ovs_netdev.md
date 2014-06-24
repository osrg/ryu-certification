---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7bd59547-36c9-4c9f-a09a-72e83f028058
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f8713aa1-bff5-4542-94c3-3e7954842676
controller          : [eae3e302-0d78-4e17-a466-09d0d38e608c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1660c6c6-1a46-451d-bc68-394e21eecdf2, 5a1fa28d-9539-4e47-8abc-dfa15c23696d, 8f179742-98a3-45e2-b193-5335487f6895, ca2d4da9-a24e-440f-8993-71466bf758b2]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : eae3e302-0d78-4e17-a466-09d0d38e608c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ca2d4da9-a24e-440f-8993-71466bf758b2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cabed6af-0250-463c-8ee8-e4473a21b33b]
name                : eth23

_uuid               : 5a1fa28d-9539-4e47-8abc-dfa15c23696d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [902b4467-e6b2-4bc4-8ba6-f44158f43930]
name                : br0

_uuid               : 1660c6c6-1a46-451d-bc68-394e21eecdf2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f03160b4-ce28-40a6-876a-d7b5d0c742ea]
name                : eth21

_uuid               : 8f179742-98a3-45e2-b193-5335487f6895
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fff817fd-c39f-43e7-8153-036529c1ea18]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f03160b4-ce28-40a6-876a-d7b5d0c742ea
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
statistics          : {collisions=0, rx_bytes=1128306399, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=89635977, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fff817fd-c39f-43e7-8153-036529c1ea18
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1400699510, tx_dropped=0, tx_errors=0, tx_packets=35340250}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : cabed6af-0250-463c-8ee8-e4473a21b33b
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=3861888580, tx_dropped=0, tx_errors=0, tx_packets=11165211}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 902b4467-e6b2-4bc4-8ba6-f44158f43930
admin_state         : down
duplex              : full
ifindex             : 651
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c424c2f734af8e59e8f5a6e6c623dfc990d58eb5
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Mon Jun 23 10:13:41 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jun 24 13:21:06 2014 -0700

    test-classifier: add ovs_assert to prevent warning
    
    GCC 4.9.0 triggers a warning &#40;array-bounds&#41; while compiling test-classifier.c
    This commit introduces an assertion that suppresses the warning.
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
