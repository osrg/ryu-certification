---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
33e9c149-0e7e-4aff-ac97-8fbb719d721f
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
_uuid               : 0425b83f-d836-44e0-9834-7f6d61afb585
controller          : [09e77722-52b5-40bd-97e4-f91efc74d7d9]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [13024b75-8914-48d6-90c7-c4b39212aef5, 4f54608c-fb2c-48cc-9378-e8c0775044f5, 6c18a9f9-7496-43cf-9fce-8a246dfaa278, 9447cbe1-8777-4b8b-b1c3-fb728026fc20]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 09e77722-52b5-40bd-97e4-f91efc74d7d9
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=696, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4f54608c-fb2c-48cc-9378-e8c0775044f5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4ee572d9-8830-47f3-be05-ece8341f719b]
name                : eth21

_uuid               : 6c18a9f9-7496-43cf-9fce-8a246dfaa278
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [013457ec-bd19-4ead-b766-f3a5b10ccda2]
name                : eth23

_uuid               : 9447cbe1-8777-4b8b-b1c3-fb728026fc20
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [87f4663a-9d2f-4801-a5da-706259e5cea1]
name                : eth22

_uuid               : 13024b75-8914-48d6-90c7-c4b39212aef5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b6a00198-a830-429b-b51e-1ee09c8429e1]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 013457ec-bd19-4ead-b766-f3a5b10ccda2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3037556908, tx_dropped=0, tx_errors=0, tx_packets=7751661}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b6a00198-a830-429b-b51e-1ee09c8429e1
admin_state         : down
duplex              : full
ifindex             : 263
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

_uuid               : 4ee572d9-8830-47f3-be05-ece8341f719b
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
statistics          : {collisions=0, rx_bytes=1549759121, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=170058784, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 87f4663a-9d2f-4801-a5da-706259e5cea1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2150761412, tx_dropped=0, tx_errors=0, tx_packets=104553653}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
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
