---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
28155adb-df52-480e-87ac-230e360c6165
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 4a8e9850-03e1-45b4-b59a-d4b45813b142
controller          : [e9c68c3f-7efb-4043-a799-8832c27de7a7]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [476ebbd9-b37a-4815-ab8b-71011eb1553f, 6a3933dc-66a9-4274-bbed-63c9b6b3ba98, 94ebc2ee-c921-440f-b091-db0b13076a08, e37814bf-f4db-4df5-a40f-16999f0103dd]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e9c68c3f-7efb-4043-a799-8832c27de7a7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=15, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6a3933dc-66a9-4274-bbed-63c9b6b3ba98
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3571966f-7190-4c9b-b004-5667fc4cd751]
name                : br0

_uuid               : 476ebbd9-b37a-4815-ab8b-71011eb1553f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4e8bd1f7-3be5-407e-ad1a-10ff0bf7e11e]
name                : eth22

_uuid               : 94ebc2ee-c921-440f-b091-db0b13076a08
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ca8d42d4-1156-4812-8e1a-1d47aa955286]
name                : eth23

_uuid               : e37814bf-f4db-4df5-a40f-16999f0103dd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [028521ef-a709-473e-99cb-fd1825b316d4]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ca8d42d4-1156-4812-8e1a-1d47aa955286
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=674416408, tx_dropped=0, tx_errors=0, tx_packets=6176234}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3571966f-7190-4c9b-b004-5667fc4cd751
admin_state         : down
ifindex             : 396
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 4e8bd1f7-3be5-407e-ad1a-10ff0bf7e11e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3882998764, tx_dropped=0, tx_errors=0, tx_packets=11199895}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 028521ef-a709-473e-99cb-fd1825b316d4
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
statistics          : {collisions=0, rx_bytes=1348541779, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=23864175, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ee088a75c65c5bc2a32887cde1c1ebc1c7fac232
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Thu Jun 5 18:54:47 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jun 5 13:08:59 2014 -0700

    ofproto: Send monitor updates if a flow mod changes a rules actions
    
    Without this change a monitor update will be sent when a flow mod changes
    a rules cookie but not if only the actions are updated. This appears
    to be a logic error.
    
    I noticed this while working on implementing OpenFlow1.4 flow monitor
    as an OpenFlow1.4 flow mod does not update a rules cookie.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
