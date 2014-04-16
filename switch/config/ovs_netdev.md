---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b609e3f1-4c90-4ddf-a4fc-397638470cb5
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1429f7ff-ea3d-4dcd-8437-b2f68b9a97bc
controller          : [b2d82d15-443c-42f2-a67f-cfe0d87d4558]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [37df5edc-cf60-4292-bd37-a5f20621e8ad, 7c57637a-e41c-4251-893b-0dc8744d491b, 99751e44-a84b-4d30-8a25-898a27d280c0]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b2d82d15-443c-42f2-a67f-cfe0d87d4558
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=537, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 37df5edc-cf60-4292-bd37-a5f20621e8ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cb7d0b18-b9e9-473d-ad13-d107c7adef15]
name                : br0

_uuid               : 99751e44-a84b-4d30-8a25-898a27d280c0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b8f0fb0f-7442-4fdb-a4e4-dbe522236699]
name                : eth8

_uuid               : 7c57637a-e41c-4251-893b-0dc8744d491b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [096580e7-3615-457f-a4be-6a1a91ecda8b]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : cb7d0b18-b9e9-473d-ad13-d107c7adef15
admin_state         : down
duplex              : full
ifindex             : 996
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : b8f0fb0f-7442-4fdb-a4e4-dbe522236699
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7494807, tx_dropped=0, tx_errors=0, tx_packets=79891}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 096580e7-3615-457f-a4be-6a1a91ecda8b
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
statistics          : {collisions=0, rx_bytes=3075999768, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72764692, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit eb7282ddfa7d9fe9ab89c7543456978e671f4335
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Wed Apr 16 08:04:23 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Wed Apr 16 08:58:53 2014 -0700

    ofproto-dpif: xlate should not attribute stats to bond entry when using recirc
    
    When recirculation is used to implement bond, the bond entry stats are
    collected from the hidden post recirculation rules. This bug causes
    double counting of stats to some strenuous bond entries.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
