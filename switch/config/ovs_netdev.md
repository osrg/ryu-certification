---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f7cc34a1-8be9-4152-8956-aeac9a6cc356
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b3921076-4f8e-4857-adde-bf52890ad3ec
controller          : [4087ecbe-84b3-4bff-8498-00f0563372c6]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [603bd911-fe1b-41ec-a369-a897136d32b1, b8aab53f-0d6f-4ce2-8c28-d561d6487ebe, e92854e6-d229-40e6-b59b-4b2a900dca10]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4087ecbe-84b3-4bff-8498-00f0563372c6
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 603bd911-fe1b-41ec-a369-a897136d32b1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b7a4c35b-9407-4ed8-b7a0-2d06e601585d]
name                : eth8

_uuid               : e92854e6-d229-40e6-b59b-4b2a900dca10
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [efff85f5-1066-434f-95ff-1d78ff19b458]
name                : eth7

_uuid               : b8aab53f-0d6f-4ce2-8c28-d561d6487ebe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9ebe08f0-3687-4e8a-b09d-26b55058e997]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9ebe08f0-3687-4e8a-b09d-26b55058e997
admin_state         : up
duplex              : full
ifindex             : 843
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

_uuid               : efff85f5-1066-434f-95ff-1d78ff19b458
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
statistics          : {collisions=0, rx_bytes=3072708512, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72731076, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : b7a4c35b-9407-4ed8-b7a0-2d06e601585d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6503653, tx_dropped=0, tx_errors=0, tx_packets=69324}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit dbdcf9ec3cf1e4de1a7dfb5e8926ba84ed929e89
Author:     Bruce Davie &lt;bsd@nicira.com&gt;
AuthorDate: Wed Apr 2 09:11:48 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Wed Apr 2 09:14:22 2014 -0700

    vtep: Add IP address configuration for bfd.
    
    The OVS implementation of BFD allows configuration of the source and
    destination IP addresses of BFD packets. This patch adds the same
    configuration option to the VTEP schema.
    
    Signed-off-by: Bruce Davie &lt;bsd@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
