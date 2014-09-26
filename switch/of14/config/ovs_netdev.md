---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b9169296-6cf6-4e59-817c-be187416b4fa
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a9d3a410-6f0b-4308-b913-6be7aaac1a1a
controller          : [1671751e-abf1-4907-8505-7a1eca64be5c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [13687b19-62e3-4da8-a5be-a7331b3235ad, 5375f8ab-649f-43eb-9f23-96aa6021eff9, b4a049b5-6157-4ffa-9a99-dd64152be139, b765f1f6-08a6-4bca-9c54-cb760d6a54e3]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1671751e-abf1-4907-8505-7a1eca64be5c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=722, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b4a049b5-6157-4ffa-9a99-dd64152be139
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bfa4488a-3cc0-469b-8ae7-9e785c9eab91]
name                : eth23

_uuid               : 13687b19-62e3-4da8-a5be-a7331b3235ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8dec2315-dc5f-46f4-ac6d-e1310a808ee8]
name                : br0

_uuid               : b765f1f6-08a6-4bca-9c54-cb760d6a54e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [693181b7-7559-4af2-a0c0-b1cc146742cb]
name                : eth22

_uuid               : 5375f8ab-649f-43eb-9f23-96aa6021eff9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f994c6eb-a120-46e5-8904-9c5c0ed1f9ff]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8dec2315-dc5f-46f4-ac6d-e1310a808ee8
admin_state         : down
duplex              : full
ifindex             : 182
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

_uuid               : bfa4488a-3cc0-469b-8ae7-9e785c9eab91
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3291006704, tx_dropped=0, tx_errors=0, tx_packets=5057316}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 693181b7-7559-4af2-a0c0-b1cc146742cb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2781398022, tx_dropped=0, tx_errors=0, tx_packets=47692805}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f994c6eb-a120-46e5-8904-9c5c0ed1f9ff
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
statistics          : {collisions=0, rx_bytes=1309186773, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=75375302, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
