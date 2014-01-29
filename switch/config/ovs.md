---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
713b03ae-4d29-4a7d-872c-cdc65c1c6a6c
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
_uuid               : 58ae5480-b489-4589-9644-8fd533666bef
controller          : [28bdadb6-72a5-4b86-8b55-1cad337e9350]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5da724a7-a198-4822-87f8-f325478251da, ad73effe-a2b2-43a9-8dd6-6e73c511a257, ee8ef84e-594c-4acb-ba3f-8d3fe3f0c15b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 28bdadb6-72a5-4b86-8b55-1cad337e9350
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ee8ef84e-594c-4acb-ba3f-8d3fe3f0c15b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6f0b7ae4-13b3-49cb-9654-6c056790bbe8]
name                : eth8

_uuid               : ad73effe-a2b2-43a9-8dd6-6e73c511a257
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0d2e8b2a-70ea-4205-ba52-ea514c6e1a39]
name                : br0

_uuid               : 5da724a7-a198-4822-87f8-f325478251da
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [289df9ef-8f12-46d7-81bf-e6b1a5d2f819]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6f0b7ae4-13b3-49cb-9654-6c056790bbe8
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

_uuid               : 0d2e8b2a-70ea-4205-ba52-ea514c6e1a39
admin_state         : up
ifindex             : 93
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

_uuid               : 289df9ef-8f12-46d7-81bf-e6b1a5d2f819
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
commit 0a8763fcb31bfca0d8d854c235c531005088fcb9
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Mon Jan 27 16:40:27 2014 -0800
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Wed Jan 29 12:31:32 2014 -0800

    ofproto-dpif-upcall: Hardcode max_idle to 1500ms.
    
    Before this patch, OVS tried to guess an optimal max idle time for
    datapath flows based on the number of datapath flows relative to the
    limit.  This caused instability because the limit was based on the
    dump duration which was affected by the max idle time.  This patch
    chooses instead to hardcode the max idle time to 1.5s except in
    extreme case where the datapath flow limit is exceeded.  1.5s was
    chosen to ensure pings occurring at once per second stay cached in the
    datapath.
    
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
