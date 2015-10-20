---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
80d7482f-8f69-4379-9056-13c0d77aaa82
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a1339f00-8aa9-4e64-a1c3-796f95617016
controller          : [c4ee8a66-a687-44ff-a397-f5f1cb7423d8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3098cfd1-ce43-4d0a-8639-17d93f671805, 35be2056-f730-4bd6-96e0-6f5095a64bd8, 77fd5d7c-60b7-4d6f-95cb-43cda441ad99, ac3c0e83-1230-48a6-90d3-50346bbffa4e]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c4ee8a66-a687-44ff-a397-f5f1cb7423d8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="752", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 77fd5d7c-60b7-4d6f-95cb-43cda441ad99
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c7ad1699-5f15-4842-9666-d1971060a32a]
name                : "eth23"

_uuid               : 3098cfd1-ce43-4d0a-8639-17d93f671805
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6c2f32fd-3843-407f-bd23-5f6524dcec89]
name                : "eth21"

_uuid               : 35be2056-f730-4bd6-96e0-6f5095a64bd8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [021324d4-9349-4126-8963-10f5c30df475]
name                : "br0"

_uuid               : ac3c0e83-1230-48a6-90d3-50346bbffa4e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f4a8f0ea-6f82-418c-b099-42882bde4462]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 021324d4-9349-4126-8963-10f5c30df475
admin_state         : down
duplex              : full
ifindex             : 587
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

_uuid               : c7ad1699-5f15-4842-9666-d1971060a32a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3971203500, tx_dropped=0, tx_errors=0, tx_packets=2647469}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 6c2f32fd-3843-407f-bd23-5f6524dcec89
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
statistics          : {collisions=0, rx_bytes=39014118128, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26040511, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f4a8f0ea-6f82-418c-b099-42882bde4462
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27717996256, tx_dropped=0, tx_errors=0, tx_packets=18492396}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6bb4a18e6c34180f42d3f55b91ac884e1b1a2da9
Author:     Justin Pettit &lt;jpettit@nicira.com&gt;
AuthorDate: Mon Oct 19 15:41:34 2015 -0700
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Mon Oct 19 16:43:53 2015 -0700

    ovn: Reduce range of ACL priorities.
    
    To implement stateful ACLs, we've needed to reserve multiple logical
    flow priorities in the ACL table.  Rather than continue to have a
    strange range of ACL priorities, we'll make ACL priority range 0 to
    32767 and then offset them by 1000 when inserting them into the logical
    flow table.
    
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
