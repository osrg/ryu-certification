---
layout: default
title: ovs_netdev - config
---

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
05e4dd1a-7e38-4cc4-a942-d90816b638f0
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : 6237dfc4-c555-49ef-befd-6ad82ac64437
controller          : [ffd38444-03b7-4ac6-926f-ac863fa8ab89]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3d428198-1dac-420c-b2cf-45f7db0c91f7, bf0e1815-742e-46d5-ab84-6b1a2acc3f14, e9fa726a-6a66-4165-ae49-863d7bcea18c]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : ffd38444-03b7-4ac6-926f-ac863fa8ab89
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 3d428198-1dac-420c-b2cf-45f7db0c91f7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b5a5becd-20f7-42b2-a917-900bbea7d010]
name                : "br0"

_uuid               : bf0e1815-742e-46d5-ab84-6b1a2acc3f14
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [757f223c-dd6b-401e-9b3a-74cd894a8a05]
name                : "eth7"

_uuid               : e9fa726a-6a66-4165-ae49-863d7bcea18c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1f718ab5-a623-4068-be6a-85835d06f26b]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 757f223c-dd6b-401e-9b3a-74cd894a8a05
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=810577, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=8309, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 1f718ab5-a623-4068-be6a-85835d06f26b
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=308350, tx_dropped=0, tx_errors=0, tx_packets=3333}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : b5a5becd-20f7-42b2-a917-900bbea7d010
admin_state         : up
duplex              : full
ifindex             : 61
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
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
commit 125bf01da3c0fba506c606ba87a2e8a8fb12d9eb
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Mon Dec 30 15:42:36 2013 -0800
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Mon Dec 30 15:42:36 2013 -0800

    tests: Make some tests more robust.
    
    These tests break if OVS internal hash function is changed.  Some of
    this is due to dependency on the order in which elements are iterated
    from hash maps, or the algorithm used is just dependent on the
    specific hash values produced for specific inputs (groups).  These
    changes make these test cases more robust, so that they will not break
    so easily due to OVS internal hash function implementation changes.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
