---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2922200a-2697-469f-a9b1-4ba682f76cb0
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b878a76d-323d-4037-a3a6-966bdcaf0d00
controller          : [8b74e870-4a50-4cfa-bbca-191f08931c63]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [37994662-e474-4e68-b7e4-e1a894cf756e, 4cfeb4b4-d44f-4591-8310-02919deaa244, be920505-5c8b-469c-add2-d0e3d439e96e, bfa3b24c-5ade-4925-ab2a-b186c4e0febe]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8b74e870-4a50-4cfa-bbca-191f08931c63
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=552, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bfa3b24c-5ade-4925-ab2a-b186c4e0febe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c99bd44e-90df-4b51-8fed-6218561a0b00]
name                : br0

_uuid               : 4cfeb4b4-d44f-4591-8310-02919deaa244
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [68301d52-0e78-45fa-952d-c3fafccff698]
name                : eth21

_uuid               : be920505-5c8b-469c-add2-d0e3d439e96e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f565a44e-1b13-4e63-8321-a9b6bfe086df]
name                : eth23

_uuid               : 37994662-e474-4e68-b7e4-e1a894cf756e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [78917bb9-1a62-4cb0-9913-c8b01bbc7534]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 78917bb9-1a62-4cb0-9913-c8b01bbc7534
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1889850576, tx_dropped=0, tx_errors=0, tx_packets=1265885}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f565a44e-1b13-4e63-8321-a9b6bfe086df
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3368907000, tx_dropped=0, tx_errors=0, tx_packets=2245938}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 68301d52-0e78-45fa-952d-c3fafccff698
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
statistics          : {collisions=0, rx_bytes=426636977, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=3163731, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c99bd44e-90df-4b51-8fed-6218561a0b00
admin_state         : down
duplex              : full
ifindex             : 175
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
commit d611866c67ba06213040b27186e402717f77d72e
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Thu May 22 14:44:36 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu May 22 11:24:45 2014 -0700

    ofproto: per-table statistics
    
    Add per-table counters. This resolves some short-comings
    in the data provided in a table stats reply message.
    
    * Lookups and matches are calculated based on table
      accesses rather than datapath flow hits and misses.
    
    * Lookups and matches are credited to the table where they
      occurred rather than all being credited to table 0.
    
    These problems were observed when running make check-ryu
    and this patch allows many of its tester.py match checks
    to pass.
    
    Reviewed-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
