---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
77586ce1-8223-4681-b260-dcf056ecf62c
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
_uuid               : 02f61e6b-1dc0-4cef-a592-7f2d0febc5e1
controller          : [c7033f76-2c2b-46ac-95a2-93dd67398f6f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [29f08366-7031-48e9-b9f9-460f1a988dd7, 4d7b397d-5585-4a8e-a882-e2d7a4707259, ab86f4db-9dc5-4605-a8c1-dda36ee8a4b3, ef5c5bfc-8d80-415b-becb-b74695fb5cfd]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c7033f76-2c2b-46ac-95a2-93dd67398f6f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ef5c5bfc-8d80-415b-becb-b74695fb5cfd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ccad99ed-d20f-48d0-9012-315db5e23601]
name                : "eth22"

_uuid               : 4d7b397d-5585-4a8e-a882-e2d7a4707259
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1f643a41-edce-419c-8247-a7ed4ae1f1e8]
name                : "eth23"

_uuid               : 29f08366-7031-48e9-b9f9-460f1a988dd7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2b7a75f6-965a-4640-8229-cd7e35d03019]
name                : "eth21"

_uuid               : ab86f4db-9dc5-4605-a8c1-dda36ee8a4b3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1bd289b1-4602-48bb-8055-7c2a43e46e57]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1bd289b1-4602-48bb-8055-7c2a43e46e57
admin_state         : down
duplex              : full
ifindex             : 806
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

_uuid               : ccad99ed-d20f-48d0-9012-315db5e23601
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31015077703, tx_dropped=0, tx_errors=0, tx_packets=20709517}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1f643a41-edce-419c-8247-a7ed4ae1f1e8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9363442500, tx_dropped=0, tx_errors=0, tx_packets=6242295}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 2b7a75f6-965a-4640-8229-cd7e35d03019
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
statistics          : {collisions=0, rx_bytes=46257528481, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30909776, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 250bd94d1e500a89c76cac944e660bd9c07ac364
Author:     Pravin B Shelar &lt;pshelar@ovn.org&gt;
AuthorDate: Thu Feb 11 01:05:16 2016 -0800
Commit:     Pravin B Shelar &lt;pshelar@ovn.org&gt;
CommitDate: Wed Feb 17 18:29:44 2016 -0800

    tunneling: Disable IPv6 tunnel
    
    There are multiple issues in IPv6 userspace tunnel
    implementation. Even the kernel module that ships with
    2.5 does not support IPv6 tunneling. There is not
    enough time to get all fixes in branch-2.5. So it make
    sense to disable the support on 2.5.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@ovn.org&gt;
    Acked-by: Flavio Leitner &lt;fbl@sysclose.org&gt;
    Acked-by: Thadeu Lima de Souza Cascardo &lt;cascardo@redhat.com&gt;
    Acked-by: Jesse Gross &lt;jesse@kernel.org&gt;
</pre>
