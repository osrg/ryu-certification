---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1c0261d7-a258-42b1-86a1-00dc333abf58
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c564e5c6-e285-4b85-8dbe-67d65508bcb8
controller          : [ab4de25d-ff13-4efd-b8bc-c2831afaf4cc]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [06d6f5ff-308f-4a76-bab6-b6153002b36c, 6b24158e-cd19-4a51-b91e-c581922ca23e, 89005c3b-8eea-46cc-a83b-319262683060]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ab4de25d-ff13-4efd-b8bc-c2831afaf4cc
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6b24158e-cd19-4a51-b91e-c581922ca23e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [182a476c-df65-4884-ba19-849cb7ae375b]
name                : eth7

_uuid               : 89005c3b-8eea-46cc-a83b-319262683060
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [36c66cc4-590c-4554-b228-8e673761f408]
name                : eth8

_uuid               : 06d6f5ff-308f-4a76-bab6-b6153002b36c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [77820259-db7e-488c-8be0-e2687800aafa]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 36c66cc4-590c-4554-b228-8e673761f408
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4474752, tx_dropped=0, tx_errors=0, tx_packets=47718}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 182a476c-df65-4884-ba19-849cb7ae375b
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
statistics          : {collisions=0, rx_bytes=3065834628, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72661315, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 77820259-db7e-488c-8be0-e2687800aafa
admin_state         : up
duplex              : full
ifindex             : 608
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
commit 543ede7e3eaac62c14a061296722839829b0cef8
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Wed Mar 19 08:51:52 2014 -0700
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Mar 19 08:51:52 2014 -0700

    lib/hmap: Remove the memory fence from hmap_is_empty().
    
    The fence made classifier_lookup() slower.  Access to a size_t 'n' is
    safe without synchonizing, and if racing with writers matters,
    additional syncronization primitives are used anyway.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
