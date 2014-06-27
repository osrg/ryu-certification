---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
74cc9bb2-e2d1-4cd1-83d6-adf0942021cf
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
_uuid               : 811ccaf6-b3b6-4afc-b685-a56c67d0c91a
controller          : [772ad412-240d-4bc7-805c-00c9fe104293]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [7b85a333-66a3-491f-b239-d6a18be4aae4, 801d1744-3e10-4f45-a574-2e4547fd8695, 8fec7a20-3813-4029-9da0-b13a13af5164, ccaf29a8-f2b4-43e6-8606-2d89660ba68b]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 772ad412-240d-4bc7-805c-00c9fe104293
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=652, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8fec7a20-3813-4029-9da0-b13a13af5164
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3bdb9068-ec4e-4850-88b4-6ba9731a0817]
name                : br0

_uuid               : ccaf29a8-f2b4-43e6-8606-2d89660ba68b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8c62acb0-6ee5-4080-8e53-f64ee18f248c]
name                : eth23

_uuid               : 801d1744-3e10-4f45-a574-2e4547fd8695
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fac18480-8bc8-4bb4-b1df-7ed0d8ef0fbc]
name                : eth22

_uuid               : 7b85a333-66a3-491f-b239-d6a18be4aae4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [89442992-24d3-4a40-b0db-f1be0d97f6f0]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8c62acb0-6ee5-4080-8e53-f64ee18f248c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=99294000, tx_dropped=0, tx_errors=0, tx_packets=66196}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fac18480-8bc8-4bb4-b1df-7ed0d8ef0fbc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=40951624, tx_dropped=0, tx_errors=0, tx_packets=27594}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3bdb9068-ec4e-4850-88b4-6ba9731a0817
admin_state         : down
ifindex             : 29
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 89442992-24d3-4a40-b0db-f1be0d97f6f0
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
statistics          : {collisions=0, rx_bytes=116876708, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=78549, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
