---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
91e56094-9c49-465d-93ec-b64e8cc4d6d4
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : 268a626d-3fd1-4cf3-901e-c5c05d6134d0
controller          : [7dc8f7c2-5e92-4ae4-a297-ec8adf4288fc]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [50de4ab0-f1c3-43ce-b542-756bb56d874f, 998cabf0-6bb9-4cd7-a986-bba73a0f0a17, f857bdea-cbaf-4efc-ab20-2534f0aefe04]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 7dc8f7c2-5e92-4ae4-a297-ec8adf4288fc
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="296", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 50de4ab0-f1c3-43ce-b542-756bb56d874f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bcd1f6e7-0100-4fc6-aa76-56b7b7918499]
name                : "eth8"

_uuid               : 998cabf0-6bb9-4cd7-a986-bba73a0f0a17
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3dd4a119-e871-496c-9eca-8a378861d434]
name                : "br0"

_uuid               : f857bdea-cbaf-4efc-ab20-2534f0aefe04
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9752c3f2-30f6-4422-923d-f48bb27b049a]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 3dd4a119-e871-496c-9eca-8a378861d434
admin_state         : up
duplex              : full
ifindex             : 53
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

_uuid               : 9752c3f2-30f6-4422-923d-f48bb27b049a
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
statistics          : {collisions=0, rx_bytes=635669, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=6523, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : bcd1f6e7-0100-4fc6-aa76-56b7b7918499
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=245290, tx_dropped=0, tx_errors=0, tx_packets=2651}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e95f1d01087ad27a71f70d8baa5c95f4350ba5bc
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Dec 5 09:21:14 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Dec 30 14:15:39 2013 -0800

    connmgr: Log when a packet-in is dropped due to queue overflow.
    
    Reported-by: Anton Matsiuk &lt;anton.matsiuk@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
