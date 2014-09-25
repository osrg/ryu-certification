---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e274ba18-f737-4a91-b4c9-bedb95c5eb10
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a20c0baa-5dc9-411b-9711-f26eec11a4e4
controller          : [60862028-e60a-4137-b439-27c314589ba2]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0cf3e208-3751-4ac9-ae95-9a29112ed7fc, 0d71e49b-3286-4f3b-91a6-7671daf412f4, 1122d7e7-c8b9-49ba-9ed8-69a703a7e084, aed1fffc-16fe-459b-87d5-ca6e63343e23]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 60862028-e60a-4137-b439-27c314589ba2
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=712, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : aed1fffc-16fe-459b-87d5-ca6e63343e23
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5b56a29e-3b7d-494a-829d-90cafd618f87]
name                : eth23

_uuid               : 0cf3e208-3751-4ac9-ae95-9a29112ed7fc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4cbaa4d2-5fa3-42f8-b76f-d11801eea151]
name                : eth21

_uuid               : 0d71e49b-3286-4f3b-91a6-7671daf412f4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a2afcb45-fd77-4245-9a3e-e716fd70024d]
name                : br0

_uuid               : 1122d7e7-c8b9-49ba-9ed8-69a703a7e084
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4657aea8-8c23-4bac-bc57-3548e768265a]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4657aea8-8c23-4bac-bc57-3548e768265a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2676223702, tx_dropped=0, tx_errors=0, tx_packets=47622103}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a2afcb45-fd77-4245-9a3e-e716fd70024d
admin_state         : down
duplex              : full
ifindex             : 178
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

_uuid               : 5b56a29e-3b7d-494a-829d-90cafd618f87
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3115658204, tx_dropped=0, tx_errors=0, tx_packets=4940417}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4cbaa4d2-5fa3-42f8-b76f-d11801eea151
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
statistics          : {collisions=0, rx_bytes=1075394357, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75218178, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit dced21add6ffb5e20594bb430fd65d4d60694d35
Author:     Simon Horman &lt;simon.horman@netronome.com&gt;
AuthorDate: Thu Sep 25 11:57:53 2014 +0000
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Thu Sep 25 13:46:50 2014 -0700

    ofproto-dpif-rid: remove unused return value of rid_pool_add&#40;&#41;
    
    The return value of rid_pool_add&#40;&#41; is never used
    so the code may be slightly simplified by removing it.
    
    Signed-off-by: Simon Horman &lt;simon.horman@netronome.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
