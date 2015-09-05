---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
422f44f5-d59f-46ec-9642-efcfc3e70e1c
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c24d54fb-2263-40ff-9aa6-bf7756eed827
controller          : [7f33acd1-e2d2-48a1-964c-b1aae0cb7308]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [716a0b27-ad71-40ce-a407-73f72bcdef59, 7b4b2ddc-2884-4a74-827d-2e43ca140106, b635f289-54fe-4b3a-a732-0f7c612d8631, dc4127ea-fc12-418d-99ed-f6420d3b6426]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7f33acd1-e2d2-48a1-964c-b1aae0cb7308
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7b4b2ddc-2884-4a74-827d-2e43ca140106
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5561577a-aea3-47d2-8424-c839594feca1]
name                : "eth22"

_uuid               : b635f289-54fe-4b3a-a732-0f7c612d8631
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8f3698e0-8a24-4d03-919b-8633c2988526]
name                : "br0"

_uuid               : dc4127ea-fc12-418d-99ed-f6420d3b6426
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9abd9474-0cef-421d-808a-d09f059253de]
name                : "eth23"

_uuid               : 716a0b27-ad71-40ce-a407-73f72bcdef59
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [069ced02-dd68-4904-95cf-91e5036a6e08]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9abd9474-0cef-421d-808a-d09f059253de
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

_uuid               : 8f3698e0-8a24-4d03-919b-8633c2988526
admin_state         : down
duplex              : full
ifindex             : 431
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

_uuid               : 069ced02-dd68-4904-95cf-91e5036a6e08
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

_uuid               : 5561577a-aea3-47d2-8424-c839594feca1
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit eac0dc83c468dc7c5b5751c96cda0e568b8b188b
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Mon Aug 31 09:53:18 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Sep 4 16:50:15 2015 -0700

    ovsdb: Update _version more accurately in transaction commit.
    
    The _version column in each OVSDB row is supposed to be updated whenever
    any other column in the row changes.  However, the transaction code was
    not careful to do this only when a row actually changed--there were other
    cases where a row was considered at transaction commit time and _version
    updated even though the row did not actually change.  For example,
    ovsdb_txn_adjust_atom_refs&#40;&#41; calls find_or_make_txn_row&#40;&#41;, which calls
    ovsdb_txn_row_modify&#40;&#41;, which updates _version, but
    ovsdb_txn_adjust_atom_refs&#40;&#41; doesn't actually update any data.
    
    One way to fix this would be to carefully consider and adjust all the code
    that looks at transaction rows.  However, this seems somewhat error prone
    and thus difficult to test.  This commit takes a different approach: it
    drops the code that adjusts _version on the fly, instead replacing it by
    a final pass over the database at the end of the commit process that checks
    for each row whether any columns changed and updates _version at that point
    if any did.  That seems pretty foolproof to me.
    
    Reported-by: RishiRaj Maulick &lt;rishi.raj2509@gmail.com&gt;
    Reported-at: http://openvswitch.org/pipermail/dev/2015-August/059439.html
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Tested-by: RishiRaj Maulick &lt;rishi.raj2509@gmail.com&gt;
</pre>
