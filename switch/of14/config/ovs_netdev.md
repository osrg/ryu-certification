---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4270a280-a00b-49c9-9843-28864077a843
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ddea635-010d-4b1f-b75e-8ff3ea5f4015
controller          : [33ec9bd0-68c9-4b83-90f6-c2db39243d79]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5be282c5-7b34-44f2-abb0-067f455f1d62, 76269f38-d372-4e1b-9ceb-b3c3b60bec43, bad68233-5570-4871-b1ef-c1e99f4d3a9d, cd0a1d95-b5e7-40c1-9af7-b2b8765b3f5e]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 33ec9bd0-68c9-4b83-90f6-c2db39243d79
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 76269f38-d372-4e1b-9ceb-b3c3b60bec43
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d3f0658b-7244-486b-b5c2-723562f2e86a]
name                : "eth22"

_uuid               : cd0a1d95-b5e7-40c1-9af7-b2b8765b3f5e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [01f28cff-404c-4091-b7e7-ba5ccf5071b6]
name                : "eth21"

_uuid               : 5be282c5-7b34-44f2-abb0-067f455f1d62
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [624bee6e-7c43-4f4a-aadf-0a20570742d9]
name                : "br0"

_uuid               : bad68233-5570-4871-b1ef-c1e99f4d3a9d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e18971cc-b76e-4f4f-b1cc-db094b2fb23d]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e18971cc-b76e-4f4f-b1cc-db094b2fb23d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6995227500, tx_dropped=0, tx_errors=0, tx_packets=4663485}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 624bee6e-7c43-4f4a-aadf-0a20570742d9
admin_state         : down
duplex              : full
ifindex             : 704
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

_uuid               : d3f0658b-7244-486b-b5c2-723562f2e86a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29593141636, tx_dropped=0, tx_errors=0, tx_packets=19752908}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 01f28cff-404c-4091-b7e7-ba5ccf5071b6
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
statistics          : {collisions=0, rx_bytes=43098052198, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28785708, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fb496f92ca1eeead8760b5cdfd857165f64deadf
Author:     Numan Siddique &lt;nusiddiq@redhat.com&gt;
AuthorDate: Mon Dec 21 12:31:14 2015 +0530
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Mon Dec 21 13:49:33 2015 -0500

    Remove broken pipe warning logs from ovsdb-server.log for ovn tests
    
    Taken the fix from the commit d3292dd... &#40;in ovn-controller-vtep.at&#41;
    
    Signed-off-by: Numan Siddique &lt;nusiddiq@redhat.com&gt;
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
</pre>
