---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f9747e82-a09c-424e-b9ad-eb15995cdd21
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
_uuid               : 541dc2e9-97eb-473e-93b6-636c903c7c0b
controller          : [75bc3927-3f28-4d33-a37b-721656a5e120]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0c6e096c-627b-4048-a39e-c5bff98bdfa2, 1e370f7b-fd56-42f3-8312-e795c2077b81, 5ae8f5d9-394d-4e35-a569-f6a4c337582e, 7babae3e-4f04-4637-8506-41bf2cb7c0e0]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 75bc3927-3f28-4d33-a37b-721656a5e120
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=666, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0c6e096c-627b-4048-a39e-c5bff98bdfa2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e1778096-d1ee-4584-ae3d-ecf7c1b3bc06]
name                : eth22

_uuid               : 5ae8f5d9-394d-4e35-a569-f6a4c337582e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8a64a9f8-9bee-4bb1-9f79-8487e739468d]
name                : eth21

_uuid               : 7babae3e-4f04-4637-8506-41bf2cb7c0e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [17db0292-3bf5-4108-a591-1275e098c849]
name                : eth23

_uuid               : 1e370f7b-fd56-42f3-8312-e795c2077b81
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [13a23a64-0ff5-4d5d-ab7a-b219c7ee0f41]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 13a23a64-0ff5-4d5d-ab7a-b219c7ee0f41
admin_state         : down
duplex              : full
ifindex             : 171
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

_uuid               : 8a64a9f8-9bee-4bb1-9f79-8487e739468d
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
statistics          : {collisions=0, rx_bytes=619509603, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74911961, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 17db0292-3bf5-4108-a591-1275e098c849
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2790030704, tx_dropped=0, tx_errors=0, tx_packets=4723332}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e1778096-d1ee-4584-ae3d-ecf7c1b3bc06
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2454830996, tx_dropped=0, tx_errors=0, tx_packets=47473436}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5d923d79ae584eaa0fac29b6d1dc3ecfca9745f1
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Sep 24 10:02:35 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Sep 24 10:07:39 2014 -0700

    AUTHORS: Add Selvamuthukumar &lt;smkumar@merunetworks.com&gt;.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
