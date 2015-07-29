---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d6c8787d-6aab-41d5-b817-5c4c295450ac
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 013d8eec-bb89-456d-928b-2709e2163685
controller          : [86c4e7e0-c402-4bef-8a6a-365c5f0af791]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0173399e-20b9-4de7-9e6f-b561b87258db, 5cf44dfe-d08a-47cf-8ca7-6ff30b2b6f77, e1ecaf58-c7cb-4cf9-808c-a6382e3d360f, ff19b72e-c62a-45e8-ac07-2eae4a92e27b]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 86c4e7e0-c402-4bef-8a6a-365c5f0af791
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e1ecaf58-c7cb-4cf9-808c-a6382e3d360f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73018831-fc33-4e86-9ac2-628c5c2c4903]
name                : "eth23"

_uuid               : 5cf44dfe-d08a-47cf-8ca7-6ff30b2b6f77
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [621f283e-2c00-4a1a-a681-486518dd16e6]
name                : "eth21"

_uuid               : ff19b72e-c62a-45e8-ac07-2eae4a92e27b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a88272de-1991-4ff2-a03f-6b7351f741b7]
name                : "br0"

_uuid               : 0173399e-20b9-4de7-9e6f-b561b87258db
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [57c7647e-ac58-452f-9379-e3a18c621478]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 73018831-fc33-4e86-9ac2-628c5c2c4903
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

_uuid               : a88272de-1991-4ff2-a03f-6b7351f741b7
admin_state         : down
duplex              : full
ifindex             : 299
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

_uuid               : 57c7647e-ac58-452f-9379-e3a18c621478
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

_uuid               : 621f283e-2c00-4a1a-a681-486518dd16e6
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
