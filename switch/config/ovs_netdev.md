---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d3548161-df7f-4c93-9926-0c6ff0dac2be
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 06b2c6b2-86e1-4855-b47f-2c005d19a5c2
controller          : [99fbd381-5d2f-4265-90ad-44093283c228]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [455be073-d487-4db4-a79c-c008095598bc, 65eb8f1c-5f9f-46a4-a0e7-bf8c76cc7124, 822fe242-c9d4-4816-ac26-b09200c124d3, efd4a959-4dfa-4604-aa56-14bcc3fc3941]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 99fbd381-5d2f-4265-90ad-44093283c228
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1002, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 65eb8f1c-5f9f-46a4-a0e7-bf8c76cc7124
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d829d78a-c914-4754-894c-c9260ea8c299]
name                : eth23

_uuid               : efd4a959-4dfa-4604-aa56-14bcc3fc3941
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [548c048b-4ebd-40a3-aa85-35ff0b70369f]
name                : eth22

_uuid               : 822fe242-c9d4-4816-ac26-b09200c124d3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c6aaaae1-e88b-44ca-a763-ae95618b3417]
name                : br0

_uuid               : 455be073-d487-4db4-a79c-c008095598bc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b2963ff5-c677-4445-a70e-a04575138bc7]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b2963ff5-c677-4445-a70e-a04575138bc7
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
statistics          : {collisions=0, rx_bytes=2530582153, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=4577541, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c6aaaae1-e88b-44ca-a763-ae95618b3417
admin_state         : down
duplex              : full
ifindex             : 236
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

_uuid               : d829d78a-c914-4754-894c-c9260ea8c299
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=614028704, tx_dropped=0, tx_errors=0, tx_packets=3272664}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 548c048b-4ebd-40a3-aa85-35ff0b70369f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2780556818, tx_dropped=0, tx_errors=0, tx_packets=1863869}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8cc868015c32dd9e9085f106c03697ea0e808c97
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Tue May 27 15:20:08 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue May 27 16:41:33 2014 -0700

    lib/flow: call memcmp in miniflow_equal&#40;&#41;
    
    This commit replace a while loop in miniflow_equal&#40;&#41; with a call to
    memcmp&#40;&#41; for performace reasons.
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
