---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
19915f59-b666-4a3f-9894-f5615a2ebad3
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6b052071-c56d-4192-b773-45cb13229e4e
controller          : [e5d1b0aa-48be-43db-a8b3-d7d365b17dd8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [03ab25fb-f215-41d2-8268-a712eae91b8f, 05a398fa-5800-4376-89e0-327db7e00ad2, 461ae596-9ab3-471d-923a-2feb8b23e3f9]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e5d1b0aa-48be-43db-a8b3-d7d365b17dd8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=537, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 461ae596-9ab3-471d-923a-2feb8b23e3f9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [79573b9e-9598-4878-b297-58278dbecdbf]
name                : eth8

_uuid               : 05a398fa-5800-4376-89e0-327db7e00ad2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ee2c1ea5-0be6-4552-8308-8e73323ac558]
name                : br0

_uuid               : 03ab25fb-f215-41d2-8268-a712eae91b8f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [52fd09cc-2fe4-43a8-b36c-fc2cd7cb832e]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 52fd09cc-2fe4-43a8-b36c-fc2cd7cb832e
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
statistics          : {collisions=0, rx_bytes=3076127857, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72766075, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : ee2c1ea5-0be6-4552-8308-8e73323ac558
admin_state         : down
duplex              : full
ifindex             : 1006
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 79573b9e-9598-4878-b297-58278dbecdbf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7543520, tx_dropped=0, tx_errors=0, tx_packets=80411}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 347bf289b3dc006ca7b95cca26d3e0d3f20fbe95
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Tue Apr 8 18:42:39 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Wed Apr 16 15:30:42 2014 -0700

    dpif-netdev: Move hash function out of the recirc action, into its own action
    
    Currently recirculation action can optionally compute hash. This patch
    adds a hash action that is independent of the recirc action, which
    no longer computes hash.  For megaflow bond with recirc, the output
    to a bond port action will look like:
    
        hash(hash_l4(0)), recirc(&lt;recirc_id&gt;)
    
    Obviously, when a recirculation application that does not depend on
    hash value can just use the recirc action alone.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Reviewed-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com
</pre>
