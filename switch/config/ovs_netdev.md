---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ab00c91a-7730-464e-857b-0d07751b6ef3
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
_uuid               : 4ebd3610-4f1d-483d-a4ee-5c5d8db8c4ea
controller          : [c32b1fe2-c214-42e9-91ae-f236eb9b4acb]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0a350639-6ab7-4d35-b824-f6dd73bbb0fa, 70e72f47-67b9-4549-b0c1-3d86856f1e7d, e89792f3-01ee-4c3d-83fb-a963b5f81edc]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c32b1fe2-c214-42e9-91ae-f236eb9b4acb
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=927, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0a350639-6ab7-4d35-b824-f6dd73bbb0fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e32a9982-f220-4abb-ac32-008b97160250]
name                : eth7

_uuid               : e89792f3-01ee-4c3d-83fb-a963b5f81edc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2289db51-7153-4d0a-8092-fd6b44417025]
name                : eth8

_uuid               : 70e72f47-67b9-4549-b0c1-3d86856f1e7d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7f48d52b-750b-4588-a2ac-e9f6f6cd36d1]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2289db51-7153-4d0a-8092-fd6b44417025
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7308948, tx_dropped=0, tx_errors=0, tx_packets=77908}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : e32a9982-f220-4abb-ac32-008b97160250
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
statistics          : {collisions=0, rx_bytes=3075420847, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72758643, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 7f48d52b-750b-4588-a2ac-e9f6f6cd36d1
admin_state         : down
duplex              : full
ifindex             : 968
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
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
commit 6105999dafd97950d8a7d9b61eda6ed2bafcc661
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Apr 10 10:24:42 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Apr 10 10:24:42 2014 -0700

    AUTHORS: Add Lior Neudorfer &lt;lior@guardicore.com&gt;.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
