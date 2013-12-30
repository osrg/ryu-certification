---
layout: default
title: ovs - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f2cc0eec-73f8-4d30-a86e-a145dc38cf6b
    Bridge "br0"
        Controller "tcp:10.24.150.30"
            is_connected: true
        fail_mode: secure
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge
_uuid               : 0c9be1df-d0c6-47c0-92ac-5a49f80cdbb7
controller          : [77c9f1d7-8edd-4fdb-9766-ad81783ee127]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [9717ec6e-c55c-4d57-a22e-635a0803a56f, a837a81c-4162-423b-81c7-c6f27e6c2934, b8f8f37f-2c3f-4990-b463-6dc4b9c387c9]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 77c9f1d7-8edd-4fdb-9766-ad81783ee127
is_connected        : true
role                : other
status              : {last_error="Connection refused", sec_since_connect="127", sec_since_disconnect="129", state=ACTIVE}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : a837a81c-4162-423b-81c7-c6f27e6c2934
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a76ec22-dfe5-44b4-bcd5-afd8e02259ee]
name                : "eth8"

_uuid               : 9717ec6e-c55c-4d57-a22e-635a0803a56f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cc06a63a-a4d4-48ee-9eac-85dfe69e8f37]
name                : "eth7"

_uuid               : b8f8f37f-2c3f-4990-b463-6dc4b9c387c9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [01db7b21-757c-4ef9-a70e-069c68106aa9]
name                : "br0"

$ sudo ovs-vsctl list Interface
_uuid               : 01db7b21-757c-4ef9-a70e-069c68106aa9
admin_state         : up
ifindex             : 37
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

_uuid               : cc06a63a-a4d4-48ee-9eac-85dfe69e8f37
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
statistics          : {collisions=0, rx_bytes=22011, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=231, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 0a76ec22-dfe5-44b4-bcd5-afd8e02259ee
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=11129, tx_dropped=0, tx_errors=0, tx_packets=120}
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
