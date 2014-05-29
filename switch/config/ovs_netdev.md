---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5af6c95e-5e93-4056-8a91-7d67ee2ddb46
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
_uuid               : c7387d21-957c-42f3-a119-2d040837eef7
controller          : [22892648-7ee2-484a-a2be-5c0254e4c5ae]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2aa38a30-9077-4453-b842-ff39bd640461, 41af7397-3310-4421-9e93-d7a68ec1f7fe, 5d9ed3b4-9fd6-47fc-8652-ce109b00d890, 5f3374b0-7a47-42f6-9253-1d970d7a9efc]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 22892648-7ee2-484a-a2be-5c0254e4c5ae
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1622, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5d9ed3b4-9fd6-47fc-8652-ce109b00d890
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [177b580e-66f4-4006-acc3-d60d315687d9]
name                : eth22

_uuid               : 2aa38a30-9077-4453-b842-ff39bd640461
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0b093d21-8e30-47d3-8cc3-adf724c61737]
name                : eth21

_uuid               : 5f3374b0-7a47-42f6-9253-1d970d7a9efc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [44b97ec4-33ce-43bb-a50d-7a0f74b2b6a2]
name                : eth23

_uuid               : 41af7397-3310-4421-9e93-d7a68ec1f7fe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d86f4bf5-b271-41db-ab38-45f1dfbb17b0]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 44b97ec4-33ce-43bb-a50d-7a0f74b2b6a2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2266137704, tx_dropped=0, tx_errors=0, tx_packets=4374070}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0b093d21-8e30-47d3-8cc3-adf724c61737
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
statistics          : {collisions=0, rx_bytes=230159497, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=5917708, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d86f4bf5-b271-41db-ab38-45f1dfbb17b0
admin_state         : down
duplex              : full
ifindex             : 286
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

_uuid               : 177b580e-66f4-4006-acc3-d60d315687d9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3504352892, tx_dropped=0, tx_errors=0, tx_packets=2349652}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6c5b90cebfea8bb88c589c76e20e7195b0c859bf
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed May 28 16:27:02 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu May 29 13:42:32 2014 -0700

    ofproto: Fix comments.
    
    The comments on the &quot;group&quot; functions had been shamelessly copied without
    significant update from the corresponding flow table functions.  This
    commit fixes the errors.
    
    This commit also removes an obsolete comment in ofopgroup_complete&#40;&#41;.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
