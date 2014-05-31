---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ef48a430-d36e-47e4-a73b-cb0790a140e9
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
_uuid               : fb4b248f-594e-480b-8453-ad6ab587ded0
controller          : [19933ecf-ffff-45ea-9bd8-3c8585d14938]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1b4ce11b-c75d-4e5c-86b5-3ba1b75719a4, 32a509ee-50d3-4d5d-a1dc-c2dc444f37e7, 930451ad-1845-4fee-97b0-7a508952fe02, dbb91bae-96f3-47d1-9722-f5ee08b532e9]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 19933ecf-ffff-45ea-9bd8-3c8585d14938
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1002, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 930451ad-1845-4fee-97b0-7a508952fe02
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [842f17c6-90a8-4310-a2f6-deb447e7914c]
name                : eth22

_uuid               : dbb91bae-96f3-47d1-9722-f5ee08b532e9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [536891e8-87c1-435c-8f7a-d0273b5ec330]
name                : eth23

_uuid               : 32a509ee-50d3-4d5d-a1dc-c2dc444f37e7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e2fc8f1a-4135-4af3-b37b-9fe86f68a3c2]
name                : br0

_uuid               : 1b4ce11b-c75d-4e5c-86b5-3ba1b75719a4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a1d73986-cb39-4bf1-a267-22180d92546c]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 536891e8-87c1-435c-8f7a-d0273b5ec330
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2962346204, tx_dropped=0, tx_errors=0, tx_packets=4838209}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 842f17c6-90a8-4310-a2f6-deb447e7914c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3789676770, tx_dropped=0, tx_errors=0, tx_packets=2541452}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e2fc8f1a-4135-4af3-b37b-9fe86f68a3c2
admin_state         : down
duplex              : full
ifindex             : 314
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

_uuid               : a1d73986-cb39-4bf1-a267-22180d92546c
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
statistics          : {collisions=0, rx_bytes=1048266186, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=6467933, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 813c5ba585f59eeffb81a185bb6e14f96bc47cc2
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Fri May 30 17:36:46 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Fri May 30 17:37:10 2014 -0700

    timeval: Import ctypes Python library within a try statement.
    
    Older versions of Python do not have ctypes as a default installed
    package. This patch puts the 'import ctypes' statement inside a try
    statement.
    
    This fixes a bug introduced by commit 8396f &#40;timeval: Use monotonic
    time in OVS Python timeval library&#41;.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
