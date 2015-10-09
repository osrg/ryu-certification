---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0737972c-bd52-441b-bd6f-335b90cd3e29
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b8682f63-dc83-4768-bd36-93088eb4f238
controller          : [f68566e8-bcee-4fde-9851-4c0b7898a535]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [17e8dc6d-1862-413e-81c7-02fa58a97081, 855904d0-e509-4acd-9a83-dcf3f8ea79b0, a85d9183-2b99-4b98-a5c2-f129768cd458, f8e1c36f-2a63-445c-8710-829861027a4a]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f68566e8-bcee-4fde-9851-4c0b7898a535
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="752", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 855904d0-e509-4acd-9a83-dcf3f8ea79b0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e8d6f52b-ee4b-46d8-a1a9-d9e50a14c4a2]
name                : "eth21"

_uuid               : 17e8dc6d-1862-413e-81c7-02fa58a97081
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4312f2b0-4ea8-4fc3-9602-e5365a4f1104]
name                : "br0"

_uuid               : f8e1c36f-2a63-445c-8710-829861027a4a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [72b99f14-3931-4d4d-aef5-1b9b58acbcac]
name                : "eth22"

_uuid               : a85d9183-2b99-4b98-a5c2-f129768cd458
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d862bd18-8d24-4c32-93be-7bd237c87597]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 72b99f14-3931-4d4d-aef5-1b9b58acbcac
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26718070606, tx_dropped=0, tx_errors=0, tx_packets=17820545}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d862bd18-8d24-4c32-93be-7bd237c87597
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2304015000, tx_dropped=0, tx_errors=0, tx_packets=1536010}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4312f2b0-4ea8-4fc3-9602-e5365a4f1104
admin_state         : down
duplex              : full
ifindex             : 549
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

_uuid               : e8d6f52b-ee4b-46d8-a1a9-d9e50a14c4a2
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
statistics          : {collisions=0, rx_bytes=36790807729, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=24546079, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f0dc83b762bd2645aef975ab01e33b8d69c68840
Author:     Ansis Atteka &lt;aatteka@nicira.com&gt;
AuthorDate: Fri Oct 2 16:46:40 2015 -0700
Commit:     Ansis Atteka &lt;aatteka@nicira.com&gt;
CommitDate: Thu Oct 8 17:32:25 2015 -0700

    RHEL: create /etc/openvswitch directory
    
    This directory needs to be created by the package manager
    because ovs-ctl is being invoked from SElinux openvswitch
    domain that does not have enough privileges to create
    directories under /etc on its own.
    
    Without this patch Open vSwitch is not able to start under
    SElinux enforcing mode &#40;which is default on CentOS by the way&#41;.
    
    Signed-off-by: Ansis Atteka &lt;aatteka@nicira.com&gt;
    Ackedy-by: Kyle Mestery &lt;mestery@mestery.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@sysclose.org&gt;
</pre>
