---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1a141111-5f10-4c70-8346-83b56645b83e
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b48cab88-5ab7-4c40-bcd7-e2063d3e18f8
controller          : [94c88c1d-53fe-4fb3-8e03-d23eb6b49c06]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2ccf2666-e503-4e55-abc5-d7f4fff1a0ac, 70084612-69e3-4c44-b262-33b78e42b2ed, c9b08a43-a2e5-4c9d-8c8f-3391394e5550, e055dd7c-6e1c-4b43-86b6-7d3173ce5f25]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 94c88c1d-53fe-4fb3-8e03-d23eb6b49c06
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="757", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e055dd7c-6e1c-4b43-86b6-7d3173ce5f25
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [06e2fe71-60d0-4198-9e1e-8bf7f5855c44]
name                : "eth22"

_uuid               : 70084612-69e3-4c44-b262-33b78e42b2ed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f911e355-f922-4980-8cd6-28db6d6b3686]
name                : "eth23"

_uuid               : 2ccf2666-e503-4e55-abc5-d7f4fff1a0ac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [942b58f0-1d64-4618-a117-4f7ef0c2390f]
name                : "eth21"

_uuid               : c9b08a43-a2e5-4c9d-8c8f-3391394e5550
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [85b628c2-26e1-4126-bb59-87d7026c8a5f]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 942b58f0-1d64-4618-a117-4f7ef0c2390f
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
statistics          : {collisions=0, rx_bytes=38077981416, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=25411271, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 06e2fe71-60d0-4198-9e1e-8bf7f5855c44
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27296703832, tx_dropped=0, tx_errors=0, tx_packets=18209330}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f911e355-f922-4980-8cd6-28db6d6b3686
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3269488500, tx_dropped=0, tx_errors=0, tx_packets=2179659}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 85b628c2-26e1-4126-bb59-87d7026c8a5f
admin_state         : down
duplex              : full
ifindex             : 571
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
