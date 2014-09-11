---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
99e0e7a5-5435-4b1a-bb48-892e1c391ddf
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8469a579-b3f7-4e28-9d4f-60025db62c16
controller          : [5b333637-689b-40c0-8c54-d445dc8f3b25]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [44925443-249c-4e63-8f16-d7a5b51149e6, 48865b68-1ac5-414e-afe8-8bae4e24dd56, 80ba9359-0547-426b-a658-4afc9cd4ae70, 81feb1ef-4f0c-47f9-b3e9-e22d47be2fc3]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b333637-689b-40c0-8c54-d445dc8f3b25
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=682, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 48865b68-1ac5-414e-afe8-8bae4e24dd56
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0814fc2f-5dd4-43d1-a649-a419a2d5aaa6]
name                : br0

_uuid               : 80ba9359-0547-426b-a658-4afc9cd4ae70
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [94a88c1f-c4d0-4ba4-a6d7-b4844f6e9e7e]
name                : eth22

_uuid               : 81feb1ef-4f0c-47f9-b3e9-e22d47be2fc3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [55eb636c-9d8b-4ed4-b6a6-39f978816fd3]
name                : eth23

_uuid               : 44925443-249c-4e63-8f16-d7a5b51149e6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [10fc205b-50f2-4987-8332-08fbd0866bcc]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 55eb636c-9d8b-4ed4-b6a6-39f978816fd3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=538872704, tx_dropped=0, tx_errors=0, tx_packets=3222560}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 10fc205b-50f2-4987-8332-08fbd0866bcc
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
statistics          : {collisions=0, rx_bytes=2336970154, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=64586559, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 94a88c1f-c4d0-4ba4-a6d7-b4844f6e9e7e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3202427072, tx_dropped=0, tx_errors=0, tx_packets=45100748}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0814fc2f-5dd4-43d1-a649-a419a2d5aaa6
admin_state         : down
duplex              : full
ifindex             : 122
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
commit 648cef14dd6775b38fb7b002d4d187a936bc8b6a
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Wed Sep 10 13:22:08 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Wed Sep 10 15:29:07 2014 -0700

    datapath: Add this_cpu_{read, inc, dec} APIs for backward compatibility
    
    The upstream modules uses this_cpu_xxx APIs. Add those functions for
    older kernel &#40;&lt;3.0.0&#41; that does not provide them.
    
    VMware-BZ: #1319082
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
