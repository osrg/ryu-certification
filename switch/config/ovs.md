---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e87f4d14-a27f-4ec1-a647-9561d899a126
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 061bf882-326a-41d3-9778-56546314aef7
controller          : [e93e70e6-4589-40c8-b53f-92212b846148]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4f904c65-95cd-4fb0-96f6-952cb742557f, 7ad17f13-10d6-472c-8fe0-efaf19fd4ca9, f28dc43a-752b-42f0-810a-81fc3d76169d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e93e70e6-4589-40c8-b53f-92212b846148
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4f904c65-95cd-4fb0-96f6-952cb742557f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [847d1a00-ad71-44d3-9f9f-0a8eea45320a]
name                : br0

_uuid               : f28dc43a-752b-42f0-810a-81fc3d76169d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4447b9c7-bbbe-4558-9aa0-693cbfd64277]
name                : eth7

_uuid               : 7ad17f13-10d6-472c-8fe0-efaf19fd4ca9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [517fec47-a95d-411f-90a9-41a5214393c7]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 847d1a00-ad71-44d3-9f9f-0a8eea45320a
admin_state         : up
ifindex             : 113
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 4447b9c7-bbbe-4558-9aa0-693cbfd64277
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 517fec47-a95d-411f-90a9-41a5214393c7
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d103f479c6a4135935f9b12f5b4f4adc91e806c3
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Fri Jan 10 15:57:04 2014 -0800
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Fri Jan 17 10:56:11 2014 -0800

    datapath: Fix kernel panic on ovs_flow_free
    
    Both mega flow mask's reference counter and per flow table mask list
    should only be accessed when holding ovs_mutex() lock. However
    this is not true with ovs_flow_table_flush(). The patch fixes this bug.
    
    Reported-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
