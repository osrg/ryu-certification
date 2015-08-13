---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b261a11e-4cc4-4ef1-841a-de966e5253b6
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ad72afbe-4adf-435b-b725-d804a3d8b3d0
controller          : [c567bd39-14a9-43c1-b713-fea771771de6]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0a76132d-7174-46f6-83b9-c041cad54a71, 8ce3cab5-264f-41ec-bda3-f00416307f89, eb6cb790-6427-4f30-a876-fe2a26fd40ea, ec59fc74-4892-4682-bae2-ff7d7090f28d]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c567bd39-14a9-43c1-b713-fea771771de6
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="6", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : eb6cb790-6427-4f30-a876-fe2a26fd40ea
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f2e8492d-a266-4ba5-92a0-7e3ac41e65b1]
name                : "br0"

_uuid               : ec59fc74-4892-4682-bae2-ff7d7090f28d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2b5f9a96-b2a8-4873-b570-7752c7db2e9f]
name                : "eth22"

_uuid               : 0a76132d-7174-46f6-83b9-c041cad54a71
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [778dd0a5-c0e6-4e5f-aa19-58b5aa94d86a]
name                : "eth21"

_uuid               : 8ce3cab5-264f-41ec-bda3-f00416307f89
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [735276c2-9fa4-4d16-b7f3-26190cc046e1]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f2e8492d-a266-4ba5-92a0-7e3ac41e65b1
admin_state         : down
duplex              : full
ifindex             : 349
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

_uuid               : 778dd0a5-c0e6-4e5f-aa19-58b5aa94d86a
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

_uuid               : 735276c2-9fa4-4d16-b7f3-26190cc046e1
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

_uuid               : 2b5f9a96-b2a8-4873-b570-7752c7db2e9f
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
commit 016e46846db5decbe6337500230cb56fd4b1bdf7
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed Aug 12 21:29:06 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Thu Aug 13 00:58:59 2015 -0700

    db-ctl-base: Allow print rows that weak reference to table in
    'cmd_show_table'.
    
    Sometimes, it is desirable to print the table with weak reference to
    the table specified in 'struct cmd_show_table'.  For example the
    Port_Binding table rows in OVN_Southbound database that refer to the
    same Chassis table row can be printed under the same chassis entry
    in 'ovn-sbctl show' output.
    
    To achieve it, this commit adds a new struct in 'struct cmd_show_table'
    that allows users to print a table with weak reference to 'table'
    specified in 'struct cmd_show_table'.  The 'ovn-sbctl' which now prints
    the Port_Binding entries with Chassis table, is the first user of this
    new feature.
    
    Requested-by: Justin Pettit &lt;jpettit@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
