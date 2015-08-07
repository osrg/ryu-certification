---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9b1078b2-21de-4b53-9a11-661112e345f4
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f0379c4-f954-49c8-a6d7-adcf26e3b471
controller          : [3d42bbf2-01af-44b3-952b-cf41930df136]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4ec684b4-e15e-4931-9c40-2952a32d04f6, accc5276-cf0f-4ceb-83d6-04e740ac502f, b56c780c-4db3-40c1-b746-438173a16520, dba99151-8cf6-49ef-ad9a-e581d40ec59a]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3d42bbf2-01af-44b3-952b-cf41930df136
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4ec684b4-e15e-4931-9c40-2952a32d04f6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [353e487c-632c-4522-848d-8a4193e3cafa]
name                : "eth21"

_uuid               : b56c780c-4db3-40c1-b746-438173a16520
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [88c45720-bb63-4ea7-88a6-f9ed7acfb83b]
name                : "eth23"

_uuid               : dba99151-8cf6-49ef-ad9a-e581d40ec59a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3ec66be1-c3eb-4c01-a58a-7e3867d6c823]
name                : "br0"

_uuid               : accc5276-cf0f-4ceb-83d6-04e740ac502f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e515e0d4-3f5f-4799-8650-f6a2cda931d6]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 88c45720-bb63-4ea7-88a6-f9ed7acfb83b
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

_uuid               : e515e0d4-3f5f-4799-8650-f6a2cda931d6
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

_uuid               : 353e487c-632c-4522-848d-8a4193e3cafa
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

_uuid               : 3ec66be1-c3eb-4c01-a58a-7e3867d6c823
admin_state         : down
duplex              : full
ifindex             : 333
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
commit 548f9fe7d28b30e18d32d60746f250bda92b7b4d
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Fri Aug 7 19:40:37 2015 +0100
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Fri Aug 7 12:58:42 2015 -0700

    Vagrantfile: Add test_ovs_system_userspace provision.
    
    Add 'test_ovs_system_userspace' provision.  Command:
            # vagrant provision --provision-with=test_ovs_system_userspace
    
    will run &quot;make check-system-userspace&quot; in the vagrant launched VM.
    
    It may be more convenient to run this tests inside a vm rather than in
    the host, because they interact with system networking.
    
    Suggested-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
