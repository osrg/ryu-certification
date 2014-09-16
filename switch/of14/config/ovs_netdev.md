---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
37796a84-0837-4b18-aab5-4b72f921bbc9
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 26b0efc9-ce84-47e1-8abb-8506c6bbb3f0
controller          : [868cda09-45e0-415b-a680-de45e49f13a4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [16d1c3e0-d20d-43d5-bee5-08303d6244b7, 9a068412-8b8d-46b5-9539-cd49aadade17, d373d13a-1216-4291-aa5d-b8347e8e538f, feaa6055-b4e3-4282-a843-4decf06fbe41]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 868cda09-45e0-415b-a680-de45e49f13a4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=697, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 16d1c3e0-d20d-43d5-bee5-08303d6244b7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [92e8911b-7077-4351-b373-5b4990ce88d5]
name                : br0

_uuid               : feaa6055-b4e3-4282-a843-4decf06fbe41
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [954d97a7-d0d9-488d-9164-d061ba85b567]
name                : eth21

_uuid               : d373d13a-1216-4291-aa5d-b8347e8e538f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7621fa56-991f-4e71-9989-7adef59051de]
name                : eth23

_uuid               : 9a068412-8b8d-46b5-9539-cd49aadade17
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e2f66ac5-f535-4bd4-b479-a8241f123b25]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e2f66ac5-f535-4bd4-b479-a8241f123b25
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3802925964, tx_dropped=0, tx_errors=0, tx_packets=45504103}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7621fa56-991f-4e71-9989-7adef59051de
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1453161704, tx_dropped=0, tx_errors=0, tx_packets=3832086}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 92e8911b-7077-4351-b373-5b4990ce88d5
admin_state         : down
duplex              : full
ifindex             : 142
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

_uuid               : 954d97a7-d0d9-488d-9164-d061ba85b567
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=3599408786, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=65434666, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5e2a670201c936e0a1f8257f4540654f8b8bfed2
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Tue Sep 16 12:45:42 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Sep 16 08:11:31 2014 -0700

    ofproto-dpif-xlate: Suppress some warnings on non-Linux OSes
    
    These warnings were introduced by
    commit 7d031d7e511aeea8dd45348922fe8e3bbdd2956e
    &#40;&quot;ofproto-dpif-xlate: Work around Linux netdev_max_backlog limit.&quot;&#41;
    and found by --enable-Werror build on NetBSD.
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
