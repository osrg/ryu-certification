---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7c4680fe-9783-4dce-8dee-895190f2aab3
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
_uuid               : 09a74ec7-7cda-49d6-95e3-2aa6d9bbc418
controller          : [77d5ebb3-42ff-4c56-bdfb-2733c0c988f2]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [d837152e-82ed-4eb0-9ae2-c2effe7f88fb, e302c136-1c2a-4377-860c-c001efdf683f, eda8136d-e201-41ae-9467-fb11e8a676a0, f31b8d08-1cc9-40c1-a3a5-f73c9ac39e4b]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 77d5ebb3-42ff-4c56-bdfb-2733c0c988f2
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=661, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f31b8d08-1cc9-40c1-a3a5-f73c9ac39e4b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [caa45d1f-ddd1-4a2f-bc8a-780f8d2004e7]
name                : eth21

_uuid               : eda8136d-e201-41ae-9467-fb11e8a676a0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [217f8f94-0387-4693-9e1e-94f714d3bff8]
name                : eth23

_uuid               : e302c136-1c2a-4377-860c-c001efdf683f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [00f6f481-c210-4ed2-89e4-938cd87968b3]
name                : br0

_uuid               : d837152e-82ed-4eb0-9ae2-c2effe7f88fb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a1e423e6-1fd9-4ab8-afef-3180e7689d98]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 217f8f94-0387-4693-9e1e-94f714d3bff8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1717962000, tx_dropped=0, tx_errors=0, tx_packets=1145308}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 00f6f481-c210-4ed2-89e4-938cd87968b3
admin_state         : down
duplex              : full
ifindex             : 59
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

_uuid               : a1e423e6-1fd9-4ab8-afef-3180e7689d98
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1329766900, tx_dropped=0, tx_errors=0, tx_packets=6618577}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : caa45d1f-ddd1-4a2f-bc8a-780f8d2004e7
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
statistics          : {collisions=0, rx_bytes=1568732041, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=9647600, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0725e74731e4ea3e49dae7200835050f0b726c88
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Aug 22 15:32:19 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Aug 25 08:54:01 2014 -0700

    ofproto-dpif-xlate: Drop 'may_learn' parameter from xlate_push_stats&#40;&#41;.
    
    Both existing callers calculated 'may_learn' as 'stats-&gt;n_packets &gt; 0', so
    it was redundant.  Because xlate_push_stats&#40;&#41; is now entirely a no-op if
    'stats-&gt;n_packets' is 0, we can now delete the tests entirely from the
    cases that previously only ran if 'may_learn'.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
