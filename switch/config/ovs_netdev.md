---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
62201072-e708-47d4-9439-3168bb4406cd
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0f09909a-079c-4f17-92cb-24e02f3f68f3
controller          : [039c1f7f-1959-4814-8a6d-d1f51d7c2657]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [061a31fb-6c0e-4695-87bd-385caf50ccf5, 22fe8876-2f19-42ed-8428-1e648412c2f8, 43166976-810c-458e-946d-390785fe3ecf, ebc3fe16-fabe-4958-8166-44ae562df07b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 039c1f7f-1959-4814-8a6d-d1f51d7c2657
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=552, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 22fe8876-2f19-42ed-8428-1e648412c2f8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30d3af5a-ee8b-42d8-951a-3dd5f0f3857c]
name                : eth21

_uuid               : ebc3fe16-fabe-4958-8166-44ae562df07b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a314746b-a5d5-470f-9f98-d57b519ecfd1]
name                : eth23

_uuid               : 43166976-810c-458e-946d-390785fe3ecf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d7c31180-65da-43ab-922f-269361515f13]
name                : br0

_uuid               : 061a31fb-6c0e-4695-87bd-385caf50ccf5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4f92e779-99a9-4bec-a3bc-52557236226f]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d7c31180-65da-43ab-922f-269361515f13
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

_uuid               : 4f92e779-99a9-4bec-a3bc-52557236226f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1374044868, tx_dropped=0, tx_errors=0, tx_packets=921641}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 30d3af5a-ee8b-42d8-951a-3dd5f0f3857c
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
statistics          : {collisions=0, rx_bytes=3328344023, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2234109, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a314746b-a5d5-470f-9f98-d57b519ecfd1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2249926500, tx_dropped=0, tx_errors=0, tx_packets=1499951}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8492d147e9662066e1e3f53b3ed7f70d5184897f
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Mon May 12 13:08:35 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Wed May 14 16:29:04 2014 -0700

    ovs-pki: Workaround lack of /dev/stdin in Windows.
    
    This lets us generate certs for unit tests on Windows
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
