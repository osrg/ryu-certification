---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
dd2a4fb8-cf63-4175-b9ac-a59f384bad03
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0130bbf7-8f1b-44a5-8cbd-a3c29835bc52
controller          : [df63d3db-9927-458c-bebe-bfdae8614ea3]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [236a1dfe-6d95-4f6a-b137-c2c17b962a60, 2734e5eb-f343-42e4-aef3-fcbff9368abf, 361dbb95-affa-4f23-a142-e09eba65eeab, 372910e9-1cb1-4646-80c3-80b405efc33a]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : df63d3db-9927-458c-bebe-bfdae8614ea3
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 372910e9-1cb1-4646-80c3-80b405efc33a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a2445162-5d69-4547-8a3f-b313c40b32ec]
name                : "br0"

_uuid               : 361dbb95-affa-4f23-a142-e09eba65eeab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5e7be6c4-39e0-48e5-bf78-4351bef78f59]
name                : "eth21"

_uuid               : 236a1dfe-6d95-4f6a-b137-c2c17b962a60
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f623b942-e6e5-4453-a237-ce695ea64fa9]
name                : "eth22"

_uuid               : 2734e5eb-f343-42e4-aef3-fcbff9368abf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [70f71924-cbf9-4a54-8088-419073cda9ac]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 70f71924-cbf9-4a54-8088-419073cda9ac
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

_uuid               : 5e7be6c4-39e0-48e5-bf78-4351bef78f59
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

_uuid               : a2445162-5d69-4547-8a3f-b313c40b32ec
admin_state         : down
duplex              : full
ifindex             : 429
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

_uuid               : f623b942-e6e5-4453-a237-ce695ea64fa9
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
