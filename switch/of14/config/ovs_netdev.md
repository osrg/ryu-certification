---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bac5aa23-c1b3-4864-a8e7-4c169cc08d28
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : cccbb851-db68-4118-ab6d-1cbd2dfe8cf9
controller          : [2b303168-78d6-4ba2-b62c-7ddcf8c6bc11]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3d40bcc9-559e-4604-8889-11ff9fac8ebf, 3eaed6cf-c959-435d-bd3e-73360717974f, 6718a3f8-435c-44f0-b008-436bbd41d69a, 8b9193da-cd14-4be0-b8df-0b2e8d2c9a4a]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2b303168-78d6-4ba2-b62c-7ddcf8c6bc11
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="752", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6718a3f8-435c-44f0-b008-436bbd41d69a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6f501692-bf54-41ce-8a93-9c479c0a3f63]
name                : "eth22"

_uuid               : 3d40bcc9-559e-4604-8889-11ff9fac8ebf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9815d36d-1a20-4d3f-9a0e-29f1a166aed9]
name                : "br0"

_uuid               : 8b9193da-cd14-4be0-b8df-0b2e8d2c9a4a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [00a70344-faf6-44a1-ac27-8a7dac757505]
name                : "eth21"

_uuid               : 3eaed6cf-c959-435d-bd3e-73360717974f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c5e28709-074d-4480-bfa0-4325fff70e70]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 00a70344-faf6-44a1-ac27-8a7dac757505
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=38195013505, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25489936, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c5e28709-074d-4480-bfa0-4325fff70e70
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3357216000, tx_dropped=0, tx_errors=0, tx_packets=2238144}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9815d36d-1a20-4d3f-9a0e-29f1a166aed9
admin_state         : down
duplex              : full
ifindex             : 573
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 6f501692-bf54-41ce-8a93-9c479c0a3f63
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27349369510, tx_dropped=0, tx_errors=0, tx_packets=18244716}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3986cae69621bd82a8945345f6345edc2407b9fd
Author:     Simon Horman &lt;simon.horman@netronome.com&gt;
AuthorDate: Fri Oct 16 19:50:47 2015 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Oct 16 08:26:12 2015 -0700

    ofproto: Correct encoding and decoding of group desc properties.
    
    * encode: if properties are present include their length in
              value of the length field of the group desc
    * decode: use the value of the length field to calculate the length of
              properties rather than assuming that the rest of the message
              is properties. This assumption is not correct as a message
              may contain multiple group descs.
    
    Fixes: 18ac06d3546e &#40;&quot;ofp-util: Encoding and decoding of &#40;draft&#41; OpenFlow 1.5 group messages.&quot;&#41;
    Signed-off-by: Simon Horman &lt;simon.horman@netronome.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
