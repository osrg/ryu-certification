---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b3a72932-4376-4429-b4fc-22bb6cd203b1
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
_uuid               : 35b6d2a9-510f-4380-83c2-0003d799b64e
controller          : [6d118484-7144-491d-866a-655873cfe1c4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [203e5fa4-244f-489b-bd01-e5751231e9db, e0923c2c-8f27-4319-9552-002ab6faec3f, f4327410-518f-49a6-8491-a377727e03e0]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6d118484-7144-491d-866a-655873cfe1c4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=941, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e0923c2c-8f27-4319-9552-002ab6faec3f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [24bc1b5f-c039-4b82-aabb-014215551e4b]
name                : eth8

_uuid               : 203e5fa4-244f-489b-bd01-e5751231e9db
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8719bf5a-b8da-4afe-9e8e-55dbfd585af3]
name                : br0

_uuid               : f4327410-518f-49a6-8491-a377727e03e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a6c35af1-0c8c-477b-8706-f7a29178bf94]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a6c35af1-0c8c-477b-8706-f7a29178bf94
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
statistics          : {collisions=0, rx_bytes=3073569638, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72739833, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 8719bf5a-b8da-4afe-9e8e-55dbfd585af3
admin_state         : down
duplex              : full
ifindex             : 887
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 24bc1b5f-c039-4b82-aabb-014215551e4b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6759589, tx_dropped=0, tx_errors=0, tx_packets=72053}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1c1764f971d470f5291a86c0f715867ce26bf321
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Thu Apr 3 17:31:03 2014 -0700
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Fri Apr 4 12:25:44 2014 -0700

    flow: Rearrange struct flow for better megaflows.
    
    Since the dp_hash will often be a hash of the 5 tuple, it makes sense
    to put it with the L4 header so it hits in the last classifier lookup
    stage.
    
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
