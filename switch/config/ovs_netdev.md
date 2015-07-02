---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a9b901bf-d529-4ee0-b10e-2b67e4727e29
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0ff7de44-fbb2-4383-984d-299c76eb1b0c
controller          : [9eb07427-ae72-48e4-8817-0a95e622e0dc]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [339077b2-d998-43e8-92a8-184452120b32, 439cb3c2-1817-42b0-a610-58fa8ce68360, b593a47f-cc8d-4be5-9748-6e33806bebbe, fe627e03-cb11-4c53-9b3c-625ed1069c08]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9eb07427-ae72-48e4-8817-0a95e622e0dc
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 339077b2-d998-43e8-92a8-184452120b32
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [33670966-f1a1-4f23-b39a-87887a4b33b4]
name                : "eth23"

_uuid               : 439cb3c2-1817-42b0-a610-58fa8ce68360
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b172e573-23a5-4250-91ae-a9aec7a9174c]
name                : "br0"

_uuid               : fe627e03-cb11-4c53-9b3c-625ed1069c08
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d3ddeaa6-84fd-4a93-8767-0fd66fc9dce4]
name                : "eth22"

_uuid               : b593a47f-cc8d-4be5-9748-6e33806bebbe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b060ca5a-4332-4a8e-803d-198704d01206]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d3ddeaa6-84fd-4a93-8767-0fd66fc9dce4
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

_uuid               : b060ca5a-4332-4a8e-803d-198704d01206
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

_uuid               : 33670966-f1a1-4f23-b39a-87887a4b33b4
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

_uuid               : b172e573-23a5-4250-91ae-a9aec7a9174c
admin_state         : down
duplex              : full
ifindex             : 212
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
commit 216e1c149a5c6d83884db447e16d30e063e1275d
Author:     Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
AuthorDate: Thu Jul 2 06:53:08 2015 +0000
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jul 2 08:35:35 2015 -0700

    datapath-windows: Solved memory leak in OVS datapath
    
    When closing opened instances, make sure the user dump state is cleared.
    
    Signed-off-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Reported-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Reported-at: https://github.com/openvswitch/ovs-issues/issues/90
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
