---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e18ad2f4-c181-4520-bedc-3bd4bc9a4dea
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
_uuid               : c7c25515-e961-40d1-b79a-d836fc5eb803
controller          : [ff9e14aa-e782-4dd5-9a87-c8fc69a2417c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0470401d-72f7-4cca-9656-a7ecf74c1ac8, 14af5e63-cfc4-4778-9bd4-04772c8d0dc8, 1bbbcce3-5d31-48e8-a428-630db1593306, f61a3b91-fa4a-43f8-bfc9-df9f2c89dd84]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ff9e14aa-e782-4dd5-9a87-c8fc69a2417c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f61a3b91-fa4a-43f8-bfc9-df9f2c89dd84
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [37501eb2-25a4-4554-807f-4900c46eaf3f]
name                : "eth22"

_uuid               : 0470401d-72f7-4cca-9656-a7ecf74c1ac8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [865566a8-f4cd-43c7-9058-13fbc1a7e165]
name                : "eth21"

_uuid               : 14af5e63-cfc4-4778-9bd4-04772c8d0dc8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [482a2b0d-ebf3-4fda-9fba-69fbe93ffcfa]
name                : "eth23"

_uuid               : 1bbbcce3-5d31-48e8-a428-630db1593306
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ec942499-2ba2-444b-974a-6726bfd04a64]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 865566a8-f4cd-43c7-9058-13fbc1a7e165
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

_uuid               : ec942499-2ba2-444b-974a-6726bfd04a64
admin_state         : down
duplex              : full
ifindex             : 331
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

_uuid               : 482a2b0d-ebf3-4fda-9fba-69fbe93ffcfa
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

_uuid               : 37501eb2-25a4-4554-807f-4900c46eaf3f
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
commit da8005a08ff7e70c1c828d69b87e8326faf21555
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Wed Jul 29 16:28:59 2015 -0700
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Fri Aug 7 11:13:26 2015 -0700

    kmod-macros: Don't unload kmod in VSWITCHD_STOP.
    
    We already queue the removal of the kernel module in OVS_VSWITCHD_START,
    via an ON_EXIT&#40;&#41; call. That command is executed in both the success and
    failure cases, so it is unnecessary to unload the kernel module in
    OVS_VSWITCHD_STOP.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
