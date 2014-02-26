---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c9cd73e3-c0d8-45ce-8791-fde1618767da
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 9cae9920-750b-49e9-b328-0efeb05933ac
controller          : [42867dc7-4835-4480-91dc-2f6812aacda3]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [47ad49e1-e2b0-402f-8207-00461951c405, 858dea57-17ee-4a0e-8d7f-a75d61996a2a, cb18e18e-ee94-4761-bd29-cbd74adff6bc]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 42867dc7-4835-4480-91dc-2f6812aacda3
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 47ad49e1-e2b0-402f-8207-00461951c405
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6986aae8-c9c7-40f8-a514-8d588a418f5b]
name                : eth8

_uuid               : cb18e18e-ee94-4761-bd29-cbd74adff6bc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b02c0e22-30e3-48dc-926b-c05f1040cb20]
name                : eth7

_uuid               : 858dea57-17ee-4a0e-8d7f-a75d61996a2a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [96a067a2-7934-49e0-9cbb-2e2736394e3e]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6986aae8-c9c7-40f8-a514-8d588a418f5b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2921898, tx_dropped=0, tx_errors=0, tx_packets=31185}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 96a067a2-7934-49e0-9cbb-2e2736394e3e
admin_state         : up
duplex              : full
ifindex             : 371
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

_uuid               : b02c0e22-30e3-48dc-926b-c05f1040cb20
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
statistics          : {collisions=0, rx_bytes=3060571177, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72607924, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5ed512094a2f5534b031d2b3873262f870dc4083
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Wed Feb 26 13:22:35 2014 -0800
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Wed Feb 26 13:23:10 2014 -0800

    dpif-linux: Lookup netdev to get netdev type string.
    
    When creating tap ports in dpif-linux, the tap type is treated the
    same as system, and the type is discarded. When dumping datapath
    port types, this would cause tap type to be reported as a system
    type.
    
    Each time we see a port of the wrong type in bridge_reconfigure(), we
    remove it and add a port with the correct configuration. This would
    always occur for tap ports, causing deletion and re-creation of all tap
    ports each time the bridge was reconfigured.
    
    This patch makes dpif-linux use netdev to look up port types if the
    datapath reports that they are of type OVS_VPORT_TYPE_NETDEV.
    
    Bug #1196289.
    
    Reported-by: James Schmidt &lt;jschmidt@vmware.com&gt;
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
