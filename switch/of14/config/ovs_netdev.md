---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0df057a1-7613-4d04-b92e-1f10148358ac
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f2607628-7dae-45fe-9ed4-e5778a06f80a
controller          : [5d49a290-4f70-4a91-b624-7ffebb26a3fa]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [88d8ff9d-2642-46fd-bb59-490ada72dc71, 90a3d442-2a30-4510-8bc0-98ecdc065152, 9610f322-12cb-4df3-b1c3-570553189af9, d97bd5d2-7461-4b33-82a0-b06fb2827c87]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5d49a290-4f70-4a91-b624-7ffebb26a3fa
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=647, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 88d8ff9d-2642-46fd-bb59-490ada72dc71
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a502dbd-16ff-4370-8934-666571bb5308]
name                : br0

_uuid               : d97bd5d2-7461-4b33-82a0-b06fb2827c87
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [752a8006-2926-449b-a9e4-d83a07d4fa51]
name                : eth22

_uuid               : 9610f322-12cb-4df3-b1c3-570553189af9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [06b3454b-0091-437b-985c-8bcbb7c4ad2f]
name                : eth21

_uuid               : 90a3d442-2a30-4510-8bc0-98ecdc065152
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4402d7d2-1a3e-4a3e-83c2-2c8581ff2d9f]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0a502dbd-16ff-4370-8934-666571bb5308
admin_state         : down
duplex              : full
ifindex             : 35
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

_uuid               : 4402d7d2-1a3e-4a3e-83c2-2c8581ff2d9f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=397455116, tx_dropped=0, tx_errors=0, tx_packets=265115}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 752a8006-2926-449b-a9e4-d83a07d4fa51
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=163632018, tx_dropped=0, tx_errors=0, tx_packets=110190}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 06b3454b-0091-437b-985c-8bcbb7c4ad2f
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
statistics          : {collisions=0, rx_bytes=467619332, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=314271, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c288d303b513f5874ea50c8845e719837ee47a23
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Fri Jun 20 13:13:51 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Jun 26 18:19:27 2014 -0700

    test-ovsdb: Workaround unicode bug in Python 2.4.x.
    
    Run the following command on Xenserver:
    PYTHONPATH=/home/ruikubo/python/compat::/home/ruikubo/python python ./tests/test-ovsdb.py     parse-atoms '{&quot;type&quot;: &quot;string&quot;, &quot;minLength&quot;: 2}'        '[&quot;&quot;]'     '[&quot;a&quot;]'     '[&quot;ab&quot;]'     '[&quot;abc&quot;]'     '[&quot;\ud834\udd1e&quot;]'
    
    And we get the following error:
    UnicodeEncodeError: 'ascii' codec can't encode character u'\U0001d11e'
    in position 23: ordinal not in range&#40;128&#41;.
    
    It looks like we are hitting the following bug:
    http://bugs.python.org/issue2517
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-By: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
