---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
74f8e232-7ab3-4feb-92cb-931214939b74
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 385b2cf2-f311-4031-8faf-422412312e09
controller          : [bdae566a-5021-437b-ae4a-1359ea5def7c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [252779c5-b4e2-4922-abf3-f5ff2e6dfd24, 3d25a97d-d316-4cf4-b3d8-d42c7d7a91f4, 5cd31b81-1625-4774-9ee1-3a289c1b1c7c, 78fd2ee6-dfd1-47cc-b655-4b5665135b70]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bdae566a-5021-437b-ae4a-1359ea5def7c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=737, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 252779c5-b4e2-4922-abf3-f5ff2e6dfd24
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [18de451b-b91a-47fb-be16-dc0b1bf3f0a9]
name                : br0

_uuid               : 5cd31b81-1625-4774-9ee1-3a289c1b1c7c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [66cd3131-8a2a-4ba8-a409-b7734db73c7b]
name                : eth23

_uuid               : 3d25a97d-d316-4cf4-b3d8-d42c7d7a91f4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b2c9b5f7-95e6-4954-903a-3b672e3312c0]
name                : eth22

_uuid               : 78fd2ee6-dfd1-47cc-b655-4b5665135b70
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [825feb88-f64f-42a3-b977-ca6aaa50e340]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 825feb88-f64f-42a3-b977-ca6aaa50e340
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
statistics          : {collisions=0, rx_bytes=1666617829, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=170137321, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 66cd3131-8a2a-4ba8-a409-b7734db73c7b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3125329408, tx_dropped=0, tx_errors=0, tx_packets=7810176}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b2c9b5f7-95e6-4954-903a-3b672e3312c0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2203210572, tx_dropped=0, tx_errors=0, tx_packets=104588912}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 18de451b-b91a-47fb-be16-dc0b1bf3f0a9
admin_state         : down
duplex              : full
ifindex             : 265
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
commit caeb4906d4f65fbb7873ee5efaf386b43f7b333d
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Fri Oct 17 17:03:13 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Fri Oct 17 17:03:13 2014 -0700

    lib/dpif-netdev: Fix EMC lookup.
    
    Patch 0de8783a9 &#40;lib/dpif-netdev: Integrate megaflow classifier.&#41;
    broke exact match cache lookup, but it went undetected since there are
    no separate stats for EMC.
    
    This patch fixes the problem by changing the struct netdev_flow_key
    'len' member to cover only the 'mf' member, not the whole
    netdev_flow_key, and ignoring the 'len' field in
    netdev_flow_key_equal.  Comparison is still accurate, as the miniflow
    'map' field encodes the length in the number of 1-bits, and the map is
    included in the comparison.
    
    Reported-by: Alex Wang &lt;alexw@nicira.com&gt;
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
</pre>
