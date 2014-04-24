---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6b479a6d-5979-400b-a5e4-7d0f790de789
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c3b6706c-5291-4fa6-aa50-ac4e5a68e34f
controller          : [0d13dccc-c470-44d6-b718-8a3fc1c9f316]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [40583593-cf67-44d2-8086-36996f50b594, b35eb758-b494-477d-8972-be1dc67f6460, c9488c40-ae80-4690-bf7a-986bfc307ca1, c986e1a8-980a-4258-b680-d18d0f49c511]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d13dccc-c470-44d6-b718-8a3fc1c9f316
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=571, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c986e1a8-980a-4258-b680-d18d0f49c511
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3b456935-5365-40f3-b0c4-6c18ddd6d403]
name                : eth21

_uuid               : c9488c40-ae80-4690-bf7a-986bfc307ca1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f1a65ed0-8bef-43eb-98c1-0bbe30a803c9]
name                : br0

_uuid               : b35eb758-b494-477d-8972-be1dc67f6460
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [95aab9ca-8fcb-491b-a84f-8e8e4cd143cf]
name                : eth23

_uuid               : 40583593-cf67-44d2-8086-36996f50b594
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ca4f52d7-6f87-4717-911e-5cf9b6e5d4da]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f1a65ed0-8bef-43eb-98c1-0bbe30a803c9
admin_state         : down
duplex              : full
ifindex             : 1129
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 3b456935-5365-40f3-b0c4-6c18ddd6d403
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=2744077452, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1844761, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 95aab9ca-8fcb-491b-a84f-8e8e4cd143cf
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1395684000, tx_dropped=0, tx_errors=0, tx_packets=930456}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ca4f52d7-6f87-4717-911e-5cf9b6e5d4da
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1643950306, tx_dropped=0, tx_errors=0, tx_packets=1102237}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 96be8de5951502c4d23f80529f4b8785aaf94f04
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Apr 23 18:33:36 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Apr 23 18:33:36 2014 -0700

    bridge: When ports disappear from a datapath, add them back.
    
    Before commit 2a73b1d73d4bdb &#40;bridge: Reconfigure in single pass.&#41;, if a
    port disappeared, for one reason or another, from a datapath, the next
    bridge reconfiguration pass would notice and, if the port was still
    configured in the database, add the port back to the datapath.  That
    commit, however, removed the logic from bridge_refresh_ofp_port&#40;&#41; that
    did that and failed to add the same logic to the replacement function
    bridge_delete_or_reconfigure_ports&#40;&#41;.  This commit fixes the problem.
    
    To see this problem on a Linux kernel system:
    
    ovs-vsctl add-br br0                             # 1
    tunctl -t tap                                    # 2
    ovs-vsctl add-port br0 tap                       # 3
    ovs-dpctl show                                   # 4
    tunctl -d tap                                    # 5
    ovs-dpctl show                                   # 6
    tunctl -t tap                                    # 7
    ovs-vsctl del-port tap -- add-port br0 tap       # 8
    ovs-dpctl show                                   # 9
    
    Steps 1-4 create a bridge and a tap and add it to the bridge and
    demonstrate that the tap is part of the datapath.  Step 5 and 6 delete
    the tap and demonstrate that it has therefore disappeared from the
    datapath.  Step 7 recreates a tap with the same name, and step 8
    forces ovs-vswitchd to reconfigure.  Step 9 shows the effect of the
    fix: without the fix, the new tap is not added back to the datapath;
    with this fix, it is.
    
    Special thanks to Gurucharan Shetty &lt;gshetty@nicira.com&gt; for finding a
    simple reproduction case and then bisecting to find the commit that
    introduced the problem.
    
    Bug #1238467.
    Reported-by: Ronald Lee &lt;ronaldlee@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
