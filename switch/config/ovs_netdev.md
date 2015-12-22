---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3860af20-6781-47e8-af2a-867d6db419fc
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7f466638-c56b-46ae-b9ad-dfe645bccaa0
controller          : [50f2b788-c59d-4f28-9f60-edd7b5930ee5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [443cf2f4-0e25-4d97-86e3-36d83bd53b3a, ca42c335-2660-4514-b2d2-99d2e1c6ef03, cd622e8c-b5ea-4d77-8792-565b7e7514e7, e1d7239c-0308-437e-8910-1df91e9ba915]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 50f2b788-c59d-4f28-9f60-edd7b5930ee5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e1d7239c-0308-437e-8910-1df91e9ba915
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e71588cf-de5a-4e25-a60b-066ccfe9dc23]
name                : "br0"

_uuid               : 443cf2f4-0e25-4d97-86e3-36d83bd53b3a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1f29180f-3ef5-4c13-a555-4f15758236b5]
name                : "eth21"

_uuid               : cd622e8c-b5ea-4d77-8792-565b7e7514e7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d2fee17a-ee1f-47a9-9c4c-1868954b7ca3]
name                : "eth23"

_uuid               : ca42c335-2660-4514-b2d2-99d2e1c6ef03
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ccab3562-c990-45cf-b7a9-ee3e19258956]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ccab3562-c990-45cf-b7a9-ee3e19258956
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29645662761, tx_dropped=0, tx_errors=0, tx_packets=19788240}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d2fee17a-ee1f-47a9-9c4c-1868954b7ca3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7083091500, tx_dropped=0, tx_errors=0, tx_packets=4722061}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1f29180f-3ef5-4c13-a555-4f15758236b5
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
statistics          : {collisions=0, rx_bytes=43215079331, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28864381, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e71588cf-de5a-4e25-a60b-066ccfe9dc23
admin_state         : down
duplex              : full
ifindex             : 706
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
commit f3d2a2957b28b7cbd0ce00945e96de1604b49e0b
Author:     Joe Stringer &lt;joe@ovn.org&gt;
AuthorDate: Mon Dec 21 15:56:40 2015 -0800
Commit:     Joe Stringer &lt;joe@ovn.org&gt;
CommitDate: Tue Dec 22 09:51:17 2015 -0800

    types: Define OVS_*128_MAX statically.
    
    The previous definitions of these variables using designated
    initializers caused a variety of issues when attempting to compile with
    MSVC, particularly if including these headers from C++ code. By defining
    them like this, we can appease MSVC and keep the definitions the same on
    all platforms.
    
    VMware-BZ: #1517163
    Suggested-by: Yin Lin &lt;linyi@vmware.com&gt;
    Signed-off-by: Joe Stringer &lt;joe@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
