---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ad376554-5b23-4b28-83f0-a884b9634f66
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : abd04759-45bc-4ab1-894b-6b112e1db83d
controller          : [9ef52952-a2f5-4dc4-8166-10f3477c87c4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [34f6df71-34f3-4e7d-ab3c-6c1ace40b04b, 687b7232-b977-4ed8-844f-965469022cf3, bb1552ad-7ab9-4110-acce-ae5dc7e49358, e83a252e-81f4-475e-8bda-5829418808f5]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9ef52952-a2f5-4dc4-8166-10f3477c87c4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=562, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bb1552ad-7ab9-4110-acce-ae5dc7e49358
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d8422f9-93c0-4fcb-b618-0618382bce2e]
name                : eth22

_uuid               : 34f6df71-34f3-4e7d-ab3c-6c1ace40b04b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5d0585b8-f3dc-4ada-a126-e0d487428253]
name                : eth21

_uuid               : 687b7232-b977-4ed8-844f-965469022cf3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ecde5424-b002-4a7a-89bb-58e9c7f864fe]
name                : eth23

_uuid               : e83a252e-81f4-475e-8bda-5829418808f5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e45eadfe-b990-4ffd-9edc-4a508934811d]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5d0585b8-f3dc-4ada-a126-e0d487428253
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
statistics          : {collisions=0, rx_bytes=3973456377, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2661206, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ecde5424-b002-4a7a-89bb-58e9c7f864fe
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2772825000, tx_dropped=0, tx_errors=0, tx_packets=1848550}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2d8422f9-93c0-4fcb-b618-0618382bce2e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1597614024, tx_dropped=0, tx_errors=0, tx_packets=1069698}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e45eadfe-b990-4ffd-9edc-4a508934811d
admin_state         : down
duplex              : full
ifindex             : 139
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d08d51b9c46e021856ec9e4aea2373e9f9b62dd2
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Tue May 20 12:44:52 2014 +1200
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Thu May 22 09:14:20 2014 +1200

    tests: Fix an ofproto test.
    
    This was previously logging that there was no such function, but passing
    the test anyway.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
