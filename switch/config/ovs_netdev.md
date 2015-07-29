---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
24b5cbc1-3b92-4878-bd00-c56acd93b5e9
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 4a2799a5-f6ca-40b0-ae24-7fe68f9d548e
controller          : [48a4ba48-ea6f-4b89-896a-0a4384f0022e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [7376c1b3-c32b-49fb-b721-fbd5f220937a, a369b2ae-b34f-47ef-b0aa-00893f65a954, c6847dd3-2157-4469-9742-86e40932c877, eaaf3987-7f8f-4c0f-8ec8-23973fbc8f5c]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 48a4ba48-ea6f-4b89-896a-0a4384f0022e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a369b2ae-b34f-47ef-b0aa-00893f65a954
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3441c8de-a9e2-419b-851a-52df4d4ec093]
name                : "br0"

_uuid               : c6847dd3-2157-4469-9742-86e40932c877
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9050f5c5-6b97-44c1-ba70-26fdd7977a60]
name                : "eth22"

_uuid               : eaaf3987-7f8f-4c0f-8ec8-23973fbc8f5c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8ec22afa-f407-4092-913b-c1e2f75eaf58]
name                : "eth23"

_uuid               : 7376c1b3-c32b-49fb-b721-fbd5f220937a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3dfd059-63ec-4e1c-9218-2dae2741b550]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9050f5c5-6b97-44c1-ba70-26fdd7977a60
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

_uuid               : b3dfd059-63ec-4e1c-9218-2dae2741b550
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

_uuid               : 8ec22afa-f407-4092-913b-c1e2f75eaf58
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

_uuid               : 3441c8de-a9e2-419b-851a-52df4d4ec093
admin_state         : down
duplex              : full
ifindex             : 297
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
commit 64e8c446ae140df25fa5976fa0a7f7c58f51ac55
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Jul 28 22:01:24 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jul 29 08:39:50 2015 -0700

    Fix treatment of OpenFlow 1.1+ bucket weights.
    
    Until now, OVS has parsed all OF1.1+ group buckets that lack a weight
    as having weight 1.  Unfortunately, OpenFlow says that only &quot;select&quot;
    groups may have a nonzero weight, and requires reporting an error for
    other kinds of groups that have a nonzero weight.  This commit fixes
    the problem by parsing only select groups with a default weight of 1
    and other groups with a default weight of 0.  It also adds the
    OpenFlow-required check for nonzero weights for other kinds of groups.
    
    This complies with OpenFlow 1.1 and later.  OF1.1 says in section 5.8:
    
        If a specified group type is invalid &#40;ie: includes fields such as
        weight that are undefined for the specified group type&#41; then the
        switch must refuse to add the group entry and must send an
        ofp_error_msg with OFPET_GROUP_MOD_FAILED type and
        OFPGMFC_INVALID_GROUP code.
    
    Found by OFTest.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@sysclose.org&gt;
</pre>
