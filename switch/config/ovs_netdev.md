---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
78823d23-cc13-4dec-a9f5-89e0cb9211f1
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8f7c4345-24af-48ac-8bee-363fa5bb6315
controller          : [1cdbeddf-7150-40f8-808a-bf80d235a3cb]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6d4ad963-c596-4d12-bf69-99926ef783b8, b063900e-02b8-4552-84d0-e93f259bed0a, b2de8bd6-4e84-4df8-85f5-1bf5d8f47fb8, fa21b69f-484a-4ef6-a6f3-1303a197fe6f]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1cdbeddf-7150-40f8-808a-bf80d235a3cb
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=666, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b2de8bd6-4e84-4df8-85f5-1bf5d8f47fb8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [974ab682-ba8d-411f-8597-930d5cb0f6c3]
name                : eth23

_uuid               : b063900e-02b8-4552-84d0-e93f259bed0a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [47300027-cfd5-4a58-b36f-4acbea6869e6]
name                : br0

_uuid               : 6d4ad963-c596-4d12-bf69-99926ef783b8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8eadc07c-c084-499b-80cd-b3a649dc1f05]
name                : eth22

_uuid               : fa21b69f-484a-4ef6-a6f3-1303a197fe6f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dea79c87-a417-4e57-bc4c-6fab58016f97]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8eadc07c-c084-499b-80cd-b3a649dc1f05
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2728845362, tx_dropped=0, tx_errors=0, tx_packets=47657477}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 974ab682-ba8d-411f-8597-930d5cb0f6c3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3203288204, tx_dropped=0, tx_errors=0, tx_packets=4998837}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 47300027-cfd5-4a58-b36f-4acbea6869e6
admin_state         : down
duplex              : full
ifindex             : 180
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

_uuid               : dea79c87-a417-4e57-bc4c-6fab58016f97
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
statistics          : {collisions=0, rx_bytes=1192289065, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75296739, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit bdcca6157dfca92a9f24da3223b87688c8f30d04
Author:     Simon Horman &lt;simon.horman@netronome.com&gt;
AuthorDate: Wed Sep 24 13:43:19 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Sep 26 10:45:06 2014 -0700

    ovs-ofctl: Correct help text for add-groups
    
    It is add-groups rather than add-group that takes FILE as an argument.
    
    Signed-off-by: Simon Horman &lt;simon.horman@netronome.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
