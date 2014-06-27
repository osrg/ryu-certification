---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ee729c1a-8feb-469e-9f07-e4c0ecfd6c90
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 10d0fb0c-1a31-494a-a786-13e7e51fdcbe
controller          : [69ac2c31-129d-46a9-be90-183ac7f4a2a1]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [13c5b97f-9f3b-4209-8d07-768dec86a217, 19932ae0-9dc6-4f40-b8c0-f3103d0780b9, 7e12de1e-23ed-4236-bdef-1f3eedffd5a7, f4c9c799-2c48-400d-8419-bce0d100fb11]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 69ac2c31-129d-46a9-be90-183ac7f4a2a1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=656, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 19932ae0-9dc6-4f40-b8c0-f3103d0780b9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e1b5eae3-c08c-4862-aef4-c4b7c84848a0]
name                : eth21

_uuid               : f4c9c799-2c48-400d-8419-bce0d100fb11
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [05c9eb96-c626-4e0c-9632-11a4cb2a20a0]
name                : eth22

_uuid               : 7e12de1e-23ed-4236-bdef-1f3eedffd5a7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8b0b6915-ad9a-4bdf-a804-42e0be0f16e8]
name                : br0

_uuid               : 13c5b97f-9f3b-4209-8d07-768dec86a217
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eb822c63-bbeb-4344-999a-b92a53a0bbf7]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8b0b6915-ad9a-4bdf-a804-42e0be0f16e8
admin_state         : down
duplex              : full
ifindex             : 33
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

_uuid               : 05c9eb96-c626-4e0c-9632-11a4cb2a20a0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=122683358, tx_dropped=0, tx_errors=0, tx_packets=82598}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : eb822c63-bbeb-4344-999a-b92a53a0bbf7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=298161116, tx_dropped=0, tx_errors=0, tx_packets=198919}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e1b5eae3-c08c-4862-aef4-c4b7c84848a0
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
statistics          : {collisions=0, rx_bytes=350739624, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=235720, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
