---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a818e331-0404-4946-9ae6-635b5bea3f4f
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
_uuid               : 7e464a98-0cb4-4c78-8264-9c43dc940189
controller          : [c4301add-8edd-4250-838e-37cf2e9896fc]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [29b2ab93-3723-4e02-a72c-040a0da01ef7, 41315d33-917a-4081-986a-a55fbe660c08, 477b442e-96c1-48b9-b38d-5e55f9a78cac, 7b19d0dd-ad8a-4a56-a251-ec384fd3a260]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c4301add-8edd-4250-838e-37cf2e9896fc
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7b19d0dd-ad8a-4a56-a251-ec384fd3a260
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [96c4cfc3-7503-4dec-9199-1c9d72e16b43]
name                : "eth21"

_uuid               : 477b442e-96c1-48b9-b38d-5e55f9a78cac
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [72813610-829a-4e9b-b918-9b0d7a094925]
name                : "eth22"

_uuid               : 29b2ab93-3723-4e02-a72c-040a0da01ef7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9259b852-eb36-4fb6-be3d-553e0c1b6864]
name                : "br0"

_uuid               : 41315d33-917a-4081-986a-a55fbe660c08
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1cb8af25-ef11-45dd-97d0-8ff0ab69388b]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 72813610-829a-4e9b-b918-9b0d7a094925
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31383771384, tx_dropped=0, tx_errors=0, tx_packets=20957558}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1cb8af25-ef11-45dd-97d0-8ff0ab69388b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9977338500, tx_dropped=0, tx_errors=0, tx_packets=6651559}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9259b852-eb36-4fb6-be3d-553e0c1b6864
admin_state         : down
duplex              : full
ifindex             : 834
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

_uuid               : 96c4cfc3-7503-4dec-9199-1c9d72e16b43
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
statistics          : {collisions=0, rx_bytes=47076615218, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31460438, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 98c23f638e706fb8d26091910e04d05992a416b2
Author:     Han Zhou &lt;zhouhan@gmail.com&gt;
AuthorDate: Thu Feb 25 23:35:35 2016 -0800
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Fri Feb 26 10:46:16 2016 -0500

    ovn-northd: Remove info log in extract_lport_addresses&#40;&#41;.
    
    When a lport is with address &quot;unknown&quot;, the function will complain
    and print misleading logs. There is no need to print the log.
    
    Signed-off-by: Han Zhou &lt;zhouhan@gmail.com&gt;
    Acked-by: Numan Siddique &lt;nusiddiq@redhat.com&gt;
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
