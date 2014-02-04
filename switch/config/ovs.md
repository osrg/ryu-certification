---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
06c0349c-6979-4611-b355-c93252825f10
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : cd72a342-50f2-4492-bdc9-6c320b932cfd
controller          : [0d7f7a75-b716-4cdb-b5f5-f8e709023824]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2e4da10e-d5b0-4f47-ac1b-bf9bcf386a69, 7af8a629-4300-4c42-a604-f671cf7f08b4, b4ef08d8-dbeb-470e-8d44-ca8a139b069b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d7f7a75-b716-4cdb-b5f5-f8e709023824
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b4ef08d8-dbeb-470e-8d44-ca8a139b069b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d35492c1-f781-4415-9d44-9c62b312068a]
name                : br0

_uuid               : 7af8a629-4300-4c42-a604-f671cf7f08b4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [45c891e0-e95f-4af7-a1cf-cb2f39152b70]
name                : eth8

_uuid               : 2e4da10e-d5b0-4f47-ac1b-bf9bcf386a69
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd76c4aa-12e2-4a7a-8b12-23eed3a07a41]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 45c891e0-e95f-4af7-a1cf-cb2f39152b70
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : d35492c1-f781-4415-9d44-9c62b312068a
admin_state         : up
ifindex             : 141
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : bd76c4aa-12e2-4a7a-8b12-23eed3a07a41
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0a0857df473cad7e8ce610f10813c94569953f98
Author:     Joe Perches &lt;joe@perches.com&gt;
AuthorDate: Mon Feb 3 17:27:41 2014 -0800
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Mon Feb 3 17:27:41 2014 -0800

    datapath: flow_netlink: Use pr_fmt to OVS_NLERR
    
    Add openvswitch:  prefix to OVS_NLERR output
    to match the other OVS_NLERR output of datapath.c
    
    Signed-off-by: Joe Perches &lt;joe@perches.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
