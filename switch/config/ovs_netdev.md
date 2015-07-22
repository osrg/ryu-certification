---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6431144f-b6de-4663-a157-2ec55ab6a65f
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 42f5f14c-6fa8-475f-adbd-23306083e5c1
controller          : [7b4996b2-06e2-4bd5-9660-f7015d1cd2a5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [494af113-9f84-4703-ae40-42c981a53f89, 896213d5-f555-42cd-a373-a7a14589a158, d6892d05-44fb-49b2-a704-ca73a8525f45, fb9eb449-d172-40bc-9b66-bfd24761f8d6]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7b4996b2-06e2-4bd5-9660-f7015d1cd2a5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d6892d05-44fb-49b2-a704-ca73a8525f45
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [25c71ff1-812e-45a2-a6ef-3fb77486d7d8]
name                : "br0"

_uuid               : fb9eb449-d172-40bc-9b66-bfd24761f8d6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [19f576bd-8b05-405c-95d3-6a2c4ed21806]
name                : "eth21"

_uuid               : 896213d5-f555-42cd-a373-a7a14589a158
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5e9b3099-2082-4b7c-a553-3d746ac5f5b5]
name                : "eth23"

_uuid               : 494af113-9f84-4703-ae40-42c981a53f89
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3b136358-8bbd-4c74-9f0f-fc812edf3e94]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3b136358-8bbd-4c74-9f0f-fc812edf3e94
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

_uuid               : 5e9b3099-2082-4b7c-a553-3d746ac5f5b5
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

_uuid               : 25c71ff1-812e-45a2-a6ef-3fb77486d7d8
admin_state         : down
duplex              : full
ifindex             : 275
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

_uuid               : 19f576bd-8b05-405c-95d3-6a2c4ed21806
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
commit 90ffd534198da1fd385082574b55d537c3881a5d
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Jul 21 11:15:06 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jul 22 09:56:32 2015 -0700

    Makefiles: Clean and do not distribute IDL-generated files.
    
    IDL-generated files don't need to be distributed, and distributing them
    puts them in the source directory rather than the build directory, which
    causes &quot;make distcheck&quot; to fail if any of them need to be remade.  To
    prevent this, this commit this removes them from ..._SOURCES, moving them
    into nodist_..._SOURCES.
    
    IDL-generated files all need to be cleaned, so this commit adds all of
    them to CLEANFILES wholesale via a single CLEANFILES += $&#40;OVSIDL_BUILT&#41;
    line in ovsdb/automake.mk, removing the individual additions from various
    makefiles.
    
    With this commit, &quot;make distcheck&quot; passes for me.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Aaron Conole &lt;aaron@bytheb.org&gt;
</pre>
