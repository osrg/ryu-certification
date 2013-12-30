---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f277b18a-ffc3-43ae-869d-f593782526a1
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
_uuid               : 5bf249fe-83bf-4c55-b8c2-9c74351f0ecd
controller          : [bfb135da-7840-4c56-835e-f389b2f88ad1]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [75310418-f252-4c1a-a4a5-8630c9505ad4, da8d0d91-d4f0-4de5-9809-5da6b86c0d39, eda7cca9-6fec-4ad0-b219-b6f4bc2c1866]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : bfb135da-7840-4c56-835e-f389b2f88ad1
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 75310418-f252-4c1a-a4a5-8630c9505ad4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [afef8b36-34b7-4cca-9528-c38edd4f2893]
name                : "br0"

_uuid               : da8d0d91-d4f0-4de5-9809-5da6b86c0d39
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c410d09e-3898-4894-983b-a47859f9cc50]
name                : "eth7"

_uuid               : eda7cca9-6fec-4ad0-b219-b6f4bc2c1866
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [530d31af-b414-48d8-8292-75479859d523]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : afef8b36-34b7-4cca-9528-c38edd4f2893
admin_state         : up
duplex              : full
ifindex             : 39
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

_uuid               : c410d09e-3898-4894-983b-a47859f9cc50
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
statistics          : {collisions=0, rx_bytes=308042, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=3184, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 530d31af-b414-48d8-8292-75479859d523
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=130392, tx_dropped=0, tx_errors=0, tx_packets=1408}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e42dfc72258c0b563a16ec36c9230287fbbcc7ae
Author:     Alin Serdean &lt;aserdean@cloudbasesolutions.com&gt;
AuthorDate: Thu Dec 19 18:23:12 2013 +0000
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Dec 27 08:03:52 2013 -0800

    Add common definitions for Windows builds.
    
    Signed-off-by: Alin Serdean &lt;aserdean at cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
