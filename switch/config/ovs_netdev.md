---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2ae501aa-c453-4da4-ae66-5be1f31ca27d
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a017ba83-79bd-4458-9a9d-688eb9e44e7b
controller          : [ddb3a6c8-234c-41e5-b920-be3fa990b26c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [188ba523-7624-4557-b54a-be0b419c6964, 78a1ec4b-032a-4cd9-bb31-462a27bc170d, 7c910e41-7487-47c8-a76e-0abc92a92e38, c6b891a5-9a3e-4193-872d-14016164d086]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ddb3a6c8-234c-41e5-b920-be3fa990b26c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=666, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c6b891a5-9a3e-4193-872d-14016164d086
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1cd8736c-02b8-46e5-a082-2f2181f328ed]
name                : eth23

_uuid               : 7c910e41-7487-47c8-a76e-0abc92a92e38
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3a37739f-a3d9-4aae-b9bd-bd988ff007cd]
name                : eth21

_uuid               : 78a1ec4b-032a-4cd9-bb31-462a27bc170d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [112b9232-7814-493c-b3e8-1c33aa8ac817]
name                : br0

_uuid               : 188ba523-7624-4557-b54a-be0b419c6964
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b1bf34a2-54b7-4999-bf43-e6d5611f8ca2]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1cd8736c-02b8-46e5-a082-2f2181f328ed
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1143631500, tx_dropped=0, tx_errors=0, tx_packets=762421}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 112b9232-7814-493c-b3e8-1c33aa8ac817
admin_state         : down
duplex              : full
ifindex             : 49
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

_uuid               : b1bf34a2-54b7-4999-bf43-e6d5611f8ca2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1204699100, tx_dropped=0, tx_errors=0, tx_packets=806676}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3a37739f-a3d9-4aae-b9bd-bd988ff007cd
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
statistics          : {collisions=0, rx_bytes=2599437943, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1740767, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c5c2c273598df7efed53fc82ad88b5bc8e2da9cf
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Thu Aug 14 21:02:15 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Aug 22 10:54:03 2014 -0700

    datapath-windows: Use OVS_DEFAULT_PORT_NO instead of 0 in a few places
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Saurabh Shah &lt;ssaurabh@vmware.com&gt;
</pre>
