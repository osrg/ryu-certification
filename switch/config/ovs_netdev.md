---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
929038f9-8602-429d-85c4-47c4341c77af
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : 960ab25a-6608-4483-8271-5e9dcc4f95af
controller          : [1871c0a3-68b4-4a4e-bbe1-df06ff962476]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [303ed9e0-fc84-4b50-b488-90652bb7f5db, 4ae9a79b-a07e-4aad-83ee-3e1c08168910, a600c989-c8a2-46ab-a594-0e9e79eaede6]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 1871c0a3-68b4-4a4e-bbe1-df06ff962476
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 303ed9e0-fc84-4b50-b488-90652bb7f5db
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fc1caf09-3663-4f80-b33f-4ad8ffbc1374]
name                : "br0"

_uuid               : a600c989-c8a2-46ab-a594-0e9e79eaede6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8668b6bd-e516-438c-93bf-5b3de493ebd6]
name                : "eth8"

_uuid               : 4ae9a79b-a07e-4aad-83ee-3e1c08168910
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cea7844c-ce9b-4dd9-8a7a-ca2e24889faf]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : cea7844c-ce9b-4dd9-8a7a-ca2e24889faf
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=723123, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=7416, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : fc1caf09-3663-4f80-b33f-4ad8ffbc1374
admin_state         : up
duplex              : full
ifindex             : 57
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 8668b6bd-e516-438c-93bf-5b3de493ebd6
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=276820, tx_dropped=0, tx_errors=0, tx_packets=2992}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ae6bde49ab95b77aa9d6dc84fdcb3d71b3d95a5c
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Mon Dec 30 14:21:40 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Dec 30 14:22:10 2013 -0800

    bridge: Fix reversed string parsing in bridge_configure_flow_miss_model().
    
    This commit fixes a command matching error introduced by commit
    7155fa52f (ofproto-dpif: Add force-miss-model configuration).
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
