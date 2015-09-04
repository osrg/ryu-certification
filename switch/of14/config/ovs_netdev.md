---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3460cf08-31e0-4cd7-8bc0-f8f2f0cccede
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 063e5830-022d-4968-9dda-7d2025f8fa3d
controller          : [7c91dd2a-a0dd-4b22-9b82-8e0467f96da6]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0e8f4e19-e9e9-474b-9720-a897881c4aa9, c30a5ed1-d916-4223-b003-5efd03713f6e, c57fa20a-da26-49d5-80de-8716845b6d26, fec08769-9be2-4896-9cf9-aeb68c7ecdc4]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7c91dd2a-a0dd-4b22-9b82-8e0467f96da6
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c30a5ed1-d916-4223-b003-5efd03713f6e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c937da49-9af6-41ea-8b8a-7e6cab5ffe0e]
name                : "eth21"

_uuid               : fec08769-9be2-4896-9cf9-aeb68c7ecdc4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [072c8950-65f5-481a-b665-cb46e99a3cce]
name                : "eth22"

_uuid               : 0e8f4e19-e9e9-474b-9720-a897881c4aa9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8c248849-5c59-4554-8e10-d72938de64b4]
name                : "eth23"

_uuid               : c57fa20a-da26-49d5-80de-8716845b6d26
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d36f1fba-7673-42c5-913a-f5145f8209bb]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 072c8950-65f5-481a-b665-cb46e99a3cce
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 8c248849-5c59-4554-8e10-d72938de64b4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c937da49-9af6-41ea-8b8a-7e6cab5ffe0e
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d36f1fba-7673-42c5-913a-f5145f8209bb
admin_state         : down
duplex              : full
ifindex             : 427
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
commit 8013510c644f4c3bc500a825a3f5e18186f18a22
Author:     Miguel Angel Ajo &lt;mangelajo@redhat.com&gt;
AuthorDate: Thu Sep 3 19:02:47 2015 +0200
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Sep 4 11:31:14 2015 -0700

    sandbox: Include vtep dir into the sandbox path
    
    Otherwise the built vtep-ctl is not available from the
    sandbox command line.
    
    Signed-off-by: Miguel Angel Ajo &lt;mangelajo@redhat.com&gt;
    Acked-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
