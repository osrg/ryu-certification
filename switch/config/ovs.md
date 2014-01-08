---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f767a99c-a57d-4ba5-b8c3-b01dfae3ed52
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge
_uuid               : 7abb25b8-452f-4909-919c-6fd585554668
controller          : [6fc73ab7-87bd-471b-8913-d414e9430d01]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [24ce3a6d-4257-461e-b05a-f0497e50fb33, db90861d-5294-4eb7-a1a3-23b7e37e76a4, ea138b12-4272-4f29-ab9a-8f791c82b1ac]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 6fc73ab7-87bd-471b-8913-d414e9430d01
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="367", sec_since_disconnect="6", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : db90861d-5294-4eb7-a1a3-23b7e37e76a4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2c0b6add-1edb-474e-9fc9-1ab3b12dca5d]
name                : "eth8"

_uuid               : 24ce3a6d-4257-461e-b05a-f0497e50fb33
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bfd7e2a2-af11-4cf3-8cbb-13a8a4df6f62]
name                : "eth7"

_uuid               : ea138b12-4272-4f29-ab9a-8f791c82b1ac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [87137c41-35b2-41e0-9907-fcede35b5f0e]
name                : "br0"

$ sudo ovs-vsctl list Interface
_uuid               : 2c0b6add-1edb-474e-9fc9-1ab3b12dca5d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 87137c41-35b2-41e0-9907-fcede35b5f0e
admin_state         : up
ifindex             : 105
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

_uuid               : bfd7e2a2-af11-4cf3-8cbb-13a8a4df6f62
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 89e45da9c16fd9dbed78feb74b1a55b332ba95a7
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Wed Jan 8 15:07:30 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jan 7 22:18:08 2014 -0800

    Fix !HAVE_NETLINK build
    
    Fix a regression introduced by commit 4b97b70d
    ("ofproto-dpif: Enable NXAST_SAMPLE only if the datapath supports it.")
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
