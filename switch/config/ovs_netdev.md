---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b68a584e-1485-456c-b158-7cff72e1c896
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
_uuid               : 96db0fac-a78b-45c4-babf-33b7398d9df1
controller          : [3402afcf-124f-489f-8d04-1f1b0d15a9c8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4e2e3054-7da5-48ca-b2ac-a60f8eb7d6ce, 9164350f-ef65-45df-b0aa-ba647aac1dfd, bceb27ce-b0ca-4b4e-a103-0c642dfc390c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3402afcf-124f-489f-8d04-1f1b0d15a9c8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4e2e3054-7da5-48ca-b2ac-a60f8eb7d6ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [96a14be1-a54f-4db6-9a2d-716081190101]
name                : eth7

_uuid               : bceb27ce-b0ca-4b4e-a103-0c642dfc390c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c9803b7f-d3c4-4f78-8ca6-bb4351c351b1]
name                : eth8

_uuid               : 9164350f-ef65-45df-b0aa-ba647aac1dfd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [08aa7db3-1479-44f1-8ccd-d64acebe9cb1]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 96a14be1-a54f-4db6-9a2d-716081190101
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
statistics          : {collisions=0, rx_bytes=3058372498, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72585609, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 08aa7db3-1479-44f1-8ccd-d64acebe9cb1
admin_state         : up
duplex              : full
ifindex             : 278
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

_uuid               : c9803b7f-d3c4-4f78-8ca6-bb4351c351b1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2274042, tx_dropped=0, tx_errors=0, tx_packets=24282}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 646f2b37ea1b98ae6887361d2f7fd6eb9cc7d94e
Author:     kmindg &lt;kmindg@gmail.com&gt;
AuthorDate: Wed Feb 19 21:45:46 2014 +0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Feb 19 11:32:17 2014 -0800

    ofp-util: Fix a typo in ofputil_decode_ofp11_port
    
    Signed-off-by: kmindg &lt;kmindg@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
