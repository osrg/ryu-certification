---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
355e6136-42c7-45da-8286-85cb7d5c5e33
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7ca8eb96-ad1f-490a-aef0-61d0a0245cd2
controller          : [d9f46ac5-301b-4592-b9f6-3aadbfa57342]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5bb7b067-7931-4110-ac68-b75db5997434, d744a05c-6097-4322-b548-129a9aeb6354, dad71516-ed9a-4f45-8b77-621b172f8eff]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d9f46ac5-301b-4592-b9f6-3aadbfa57342
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d744a05c-6097-4322-b548-129a9aeb6354
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9afe599c-3443-464f-b7d3-429f0b8fca47]
name                : br0

_uuid               : dad71516-ed9a-4f45-8b77-621b172f8eff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [82f27955-5042-443c-b26d-8a72bf4b6e27]
name                : eth8

_uuid               : 5bb7b067-7931-4110-ac68-b75db5997434
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bcc6fe70-d0e1-462c-b3f5-c3496af4b7a4]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9afe599c-3443-464f-b7d3-429f0b8fca47
admin_state         : up
ifindex             : 98
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : bcc6fe70-d0e1-462c-b3f5-c3496af4b7a4
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 82f27955-5042-443c-b26d-8a72bf4b6e27
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 59804c80a9821e3aca208012c1a496f3c26bfe9a
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Jan 30 16:57:16 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jan 30 16:57:16 2014 -0800

    bridge: Set ofport column in every database transaction.
    
    Database transactions can occasionally fail due to concurrent changes in
    the database.  When that happens, the next transaction should repeat the
    changes that ovs-vswitchd tried to make the first time (adjusted for the
    changes to the database).
    
    The code to report the OpenFlow port number in use didn't do that.  It set
    the ofport field once when it created the port and never set it again, even
    if the transaction to set it failed.  This commit fixes the problem.
    
    Bug #23047.
    Reported-by: Suganya Ramachandran &lt;suganyar@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
