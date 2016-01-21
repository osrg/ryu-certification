---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
217731f1-6697-496f-9f55-5ac783fac1e8
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0ee693c3-28d4-4453-98ce-4993dc60364a
controller          : [59dcba69-b663-4afa-992c-c4465acf4252]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [04e74907-5a22-4c1e-83ec-42b32d679122, 3470805f-6177-4a3d-ab41-fe378411a38e, 5bc691d3-f414-4bd0-a347-cd86ac767263, d445de30-2b7b-4dc3-a630-eecf1e5fab40]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 59dcba69-b663-4afa-992c-c4465acf4252
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d445de30-2b7b-4dc3-a630-eecf1e5fab40
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [acf6025e-cebc-4439-ad6b-a79820d26842]
name                : "eth23"

_uuid               : 04e74907-5a22-4c1e-83ec-42b32d679122
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [108f3446-c2a7-46b4-ac42-36777102a782]
name                : "eth22"

_uuid               : 5bc691d3-f414-4bd0-a347-cd86ac767263
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a92b5cba-f220-4455-bf73-14e3aae8b046]
name                : "eth21"

_uuid               : 3470805f-6177-4a3d-ab41-fe378411a38e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9ac6fa60-bfa3-40b1-843b-108209522850]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9ac6fa60-bfa3-40b1-843b-108209522850
admin_state         : down
duplex              : full
ifindex             : 722
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

_uuid               : acf6025e-cebc-4439-ad6b-a79820d26842
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7433925000, tx_dropped=0, tx_errors=0, tx_packets=4955950}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 108f3446-c2a7-46b4-ac42-36777102a782
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29856336293, tx_dropped=0, tx_errors=0, tx_packets=19929972}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a92b5cba-f220-4455-bf73-14e3aae8b046
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
statistics          : {collisions=0, rx_bytes=43683151395, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29179060, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit aa07423103f0593e040240313f94e89ad43e674c
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Thu Jan 21 14:07:50 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Thu Jan 21 15:41:55 2016 -0500

    travis: Install six Python library.
    
    The travis-ci build is broken because the Python six library is not
    installed.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Tested-by: Joe Stringer &lt;joe@ovn.org&gt;
    Acked-by: Joe Stringer &lt;joe@ovn.org&gt;
</pre>
