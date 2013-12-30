---
layout: default
title: ovs - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
63e0f4f0-aa2d-4e3f-9242-eb7e3153535b
    Bridge "br0"
        Controller "tcp:10.24.150.30"
            is_connected: true
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "eth7"
            Interface "eth7"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge
_uuid               : 1bc753a2-1999-414c-b6aa-a5efb64fbb2b
controller          : [30a274f5-1e3d-4923-bab6-3456c74ed33f]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [8b8aa27e-14e6-4c91-993d-a802ae0038ae, a6080a70-0846-422c-94af-9cac2da10749, dc013dde-83f9-4233-a8fa-0c1d87603970]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 30a274f5-1e3d-4923-bab6-3456c74ed33f
is_connected        : true
role                : other
status              : {last_error="Connection refused", sec_since_connect="121", sec_since_disconnect="123", state=ACTIVE}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : a6080a70-0846-422c-94af-9cac2da10749
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0e0f6b16-5d5f-4ad2-b293-8e24f99a6347]
name                : "eth7"

_uuid               : dc013dde-83f9-4233-a8fa-0c1d87603970
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [57c0af6d-abfa-48aa-bd98-9a93379954d9]
name                : "br0"

_uuid               : 8b8aa27e-14e6-4c91-993d-a802ae0038ae
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f15f1afa-2351-4daa-9fc7-aecd03630a11]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 57c0af6d-abfa-48aa-bd98-9a93379954d9
admin_state         : up
ifindex             : 51
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 0e0f6b16-5d5f-4ad2-b293-8e24f99a6347
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
statistics          : {collisions=0, rx_bytes=21528, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=225, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : f15f1afa-2351-4daa-9fc7-aecd03630a11
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10964, tx_dropped=0, tx_errors=0, tx_packets=118}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0cf3b0d0fd97c52822979fe7cf1e594be03324a9
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Dec 20 15:12:58 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Dec 30 13:45:33 2013 -0800

    ofproto-dpif-monitor: Remove monitor_init().
    
    Commit 881d47a9fa9 (monitor: Replace monitor_seq with periodic
    wakeup.) removes the global "struct seq" in ofproto-dpif-monitor
    module.  This change makes the monitor_init() no longer needed.
    
    This commit removes the monitor_init() from ofproto-dpif-monitor.c.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
