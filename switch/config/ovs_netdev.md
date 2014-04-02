---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
00006bc0-da03-48a4-b577-74f09e5fd2d5
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 928046c7-5d6c-496e-b7d5-93ef5fd3ea03
controller          : [df6e9ca3-29f5-4093-8cf7-5c8caf05469b]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [49b30c12-0bea-4a57-8d2f-35e34d376ee3, 6c220ec4-3130-41fc-b866-d15a119f888f, f9ef2811-fa5c-4d55-9154-5d492f4263db]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : df6e9ca3-29f5-4093-8cf7-5c8caf05469b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=312, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6c220ec4-3130-41fc-b866-d15a119f888f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d0fc7cc6-1e52-4ac9-a11b-20d52e528e3e]
name                : eth8

_uuid               : f9ef2811-fa5c-4d55-9154-5d492f4263db
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f3969846-a6e2-45a6-ab35-6a20ca8ccb85]
name                : br0

_uuid               : 49b30c12-0bea-4a57-8d2f-35e34d376ee3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eda46916-569b-41b0-aeb4-8cc5ccd0c248]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d0fc7cc6-1e52-4ac9-a11b-20d52e528e3e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6552366, tx_dropped=0, tx_errors=0, tx_packets=69844}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : eda46916-569b-41b0-aeb4-8cc5ccd0c248
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
statistics          : {collisions=0, rx_bytes=3072875151, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72732775, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : f3969846-a6e2-45a6-ab35-6a20ca8ccb85
admin_state         : up
duplex              : full
ifindex             : 853
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1af09488c1d11b7980760a32d280506dc23ac32f
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Apr 2 15:03:41 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Apr 2 15:03:41 2014 -0700

    ovsdb-client: Support all vlog options.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
