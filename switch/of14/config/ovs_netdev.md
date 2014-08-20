---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cd806581-c922-4d7c-a9de-c66549afa37e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : de9d1318-6617-42fa-8c86-2e1c57e89c3b
controller          : [e447fba6-3f1f-4473-823c-aa38bd23c049]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [13c65c28-f49a-47a6-bcea-387d5f52bcda, 4d127353-0601-4669-89af-d41dcb926e68, 7b0f4b8e-1eb0-4b8c-aac3-e35e3d4c8f09, f4d803c8-e056-412f-b73a-099886ea5754]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e447fba6-3f1f-4473-823c-aa38bd23c049
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=687, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 13c65c28-f49a-47a6-bcea-387d5f52bcda
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ff57bac5-a11f-4c31-a1b5-ea5a9427af27]
name                : eth21

_uuid               : f4d803c8-e056-412f-b73a-099886ea5754
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ccb58753-5763-46f7-88ad-fdc7654ed414]
name                : eth23

_uuid               : 7b0f4b8e-1eb0-4b8c-aac3-e35e3d4c8f09
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [41454d11-3cb7-478e-bf1c-e23f8cc5cce2]
name                : br0

_uuid               : 4d127353-0601-4669-89af-d41dcb926e68
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ce03e19c-8d40-4685-9f57-8866ad50d02e]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ce03e19c-8d40-4685-9f57-8866ad50d02e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=411864712, tx_dropped=0, tx_errors=0, tx_packets=277015}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 41454d11-3cb7-478e-bf1c-e23f8cc5cce2
admin_state         : down
duplex              : full
ifindex             : 43
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

_uuid               : ff57bac5-a11f-4c31-a1b5-ea5a9427af27
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
statistics          : {collisions=0, rx_bytes=1028574216, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=690935, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ccb58753-5763-46f7-88ad-fdc7654ed414
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=822313500, tx_dropped=0, tx_errors=0, tx_packets=548209}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 09e256031a62f8c3067563140d3f7cf30b0f1c85
Author:     Terry Wilson &lt;twilson@redhat.com&gt;
AuthorDate: Tue Aug 19 17:28:55 2014 -0600
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Aug 20 10:25:35 2014 -0700

    ovsdb: Allow comparison on optional scalar types
    
    This allows things like initiating a wait request on an interface
    ofport being set.
    
    When the optional field is empty and operation is != or excludes
    then the result is true; otherwise it is false. If the field is
    set then the field is compared normally for its type.
    
    Signed-off-by: Terry Wilson &lt;twilson@redhat.com&gt;
    [blp@nicira.com updated ovsdb-server&#40;1&#41; and NEWS.]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
