---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e4886d8e-511d-466c-9564-6665a0cdff00
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
_uuid               : 2a60ff87-bf75-4bcc-8d4f-a1298d98e75c
controller          : [80b01e61-b1bc-4b6a-82ee-02515d0d623b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [038dfc90-e162-4ecd-b675-b31ac892398f, b40d2c38-e6fa-469e-994f-a006ca0dc9e1, d9ec900f-fc32-4aa0-9d15-c691ffb73037]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 80b01e61-b1bc-4b6a-82ee-02515d0d623b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 038dfc90-e162-4ecd-b675-b31ac892398f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [257f68c5-e959-4a4a-a2df-782806262b7b]
name                : "br0"

_uuid               : b40d2c38-e6fa-469e-994f-a006ca0dc9e1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a80027e6-aed6-4179-83b2-d8c82839b88a]
name                : "eth7"

_uuid               : d9ec900f-fc32-4aa0-9d15-c691ffb73037
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7f6983f7-fbc5-4fde-9853-69cc8e8e9729]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 257f68c5-e959-4a4a-a2df-782806262b7b
admin_state         : up
duplex              : full
ifindex             : 97
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

_uuid               : a80027e6-aed6-4179-83b2-d8c82839b88a
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
statistics          : {collisions=0, rx_bytes=1942271, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=19762, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 7f6983f7-fbc5-4fde-9853-69cc8e8e9729
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=666632, tx_dropped=0, tx_errors=0, tx_packets=7194}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fe68c005871ec5b4b3f33c1b99593667cc83c234
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Tue Jan 7 14:33:37 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jan 7 14:53:25 2014 -0800

    netdev: Update rx_recv documentation for NULL case
    
    Replace truncated description of when rx_recv() may be NULL
    with text used for other fields of netdev_class.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
