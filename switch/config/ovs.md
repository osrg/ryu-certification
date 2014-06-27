---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d78d288e-a95c-408c-ad4a-9f8f83fe2212
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 4a0ad338-cc2e-4766-b5e1-5597a546f400
controller          : [2083d154-5ea2-4b9b-a13d-2071d1c952b7]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [405b2803-6606-449c-b50c-2ea2fab83cf6, 61c42059-0b9c-4328-929b-63ebb98467a5, abb7fadf-d934-481b-8323-784d1618e7cb, f90b6923-d7af-48ca-af92-bbe4cf4a4687]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2083d154-5ea2-4b9b-a13d-2071d1c952b7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=1107, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 61c42059-0b9c-4328-929b-63ebb98467a5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2858e569-e3f6-4665-a72f-84ebb61c00fb]
name                : eth22

_uuid               : abb7fadf-d934-481b-8323-784d1618e7cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5449aa28-805a-47da-9bcb-56cd1143c3cd]
name                : eth23

_uuid               : f90b6923-d7af-48ca-af92-bbe4cf4a4687
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c7c8bb39-bd88-456c-ba76-0bad77c72901]
name                : br0

_uuid               : 405b2803-6606-449c-b50c-2ea2fab83cf6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c97bcc7f-40c3-4bec-b9bf-7084cb1ff771]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5449aa28-805a-47da-9bcb-56cd1143c3cd
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=198733616, tx_dropped=0, tx_errors=0, tx_packets=132634}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c7c8bb39-bd88-456c-ba76-0bad77c72901
admin_state         : down
ifindex             : 31
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

_uuid               : 2858e569-e3f6-4665-a72f-84ebb61c00fb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=81844198, tx_dropped=0, tx_errors=0, tx_packets=55079}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c97bcc7f-40c3-4bec-b9bf-7084cb1ff771
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
statistics          : {collisions=0, rx_bytes=233835916, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=157153, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
