---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6f0beb35-a3bc-407f-9871-62d368668007
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 06a7f9b2-ac54-4055-b57d-a32d960f0832
controller          : [cc0faa27-9102-444e-8c62-590c23a00802]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0af0e26b-8a4f-4a95-85dd-49c2f17cfa31, 730ac23d-efb2-4550-a8db-77cb38ee4848, c5bc7b00-c004-42ba-9a1d-afebe9c63eb1]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cc0faa27-9102-444e-8c62-590c23a00802
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c5bc7b00-c004-42ba-9a1d-afebe9c63eb1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dc470c18-5c74-4777-96b9-649bc22f63cb]
name                : eth7

_uuid               : 730ac23d-efb2-4550-a8db-77cb38ee4848
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4072bf15-99d6-4941-ba3e-0f127aacffb5]
name                : eth8

_uuid               : 0af0e26b-8a4f-4a95-85dd-49c2f17cfa31
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d726ffe3-4ac5-4c7b-9b1d-252dc40be02e]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dc470c18-5c74-4777-96b9-649bc22f63cb
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
statistics          : {collisions=0, rx_bytes=3057519571, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72577024, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 4072bf15-99d6-4941-ba3e-0f127aacffb5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1994144, tx_dropped=0, tx_errors=0, tx_packets=21299}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : d726ffe3-4ac5-4c7b-9b1d-252dc40be02e
admin_state         : up
duplex              : full
ifindex             : 254
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 97ba2d36f659170fc5645c47c928041d5c8f51e8
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Wed Feb 12 09:27:11 2014 -0800
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Thu Feb 13 14:05:55 2014 -0800

    ofproto-dpif: Use adaptive mutex for stats.
    
    Stats critical sections are held for very short time, so it makes
    sense to spin on them for a while rather than sleeping immediately.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
