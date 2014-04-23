---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a3840882-4528-472b-98cc-85470fa4be3a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6fe762f9-c5e2-4a2a-b4ef-82ed9993c3a9
controller          : [a5b4ef36-386d-4537-8812-c04d7fde8bc3]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [25d2925a-b612-4cdf-b5a9-fed659383c91, 6fedb8d0-8717-45c2-b554-db91e74576ab, 8f8e4052-9405-4b6e-9231-850da9cd4acd, f4d295bd-f7f9-4f8a-bcf9-f7456180291a]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a5b4ef36-386d-4537-8812-c04d7fde8bc3
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=577, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6fedb8d0-8717-45c2-b554-db91e74576ab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1c21b8b6-e5db-41cc-8c9e-47fc2b9d55ba]
name                : br0

_uuid               : f4d295bd-f7f9-4f8a-bcf9-f7456180291a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8cb2002b-1010-4b14-b32c-70d30ec42715]
name                : eth21

_uuid               : 25d2925a-b612-4cdf-b5a9-fed659383c91
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [03ee55ea-383a-4d43-a8b3-4a3d144a0526]
name                : eth22

_uuid               : 8f8e4052-9405-4b6e-9231-850da9cd4acd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [037d4d09-1790-4625-939e-7aa39ba6099e]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 037d4d09-1790-4625-939e-7aa39ba6099e
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1191142500, tx_dropped=0, tx_errors=0, tx_packets=794095}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 03ee55ea-383a-4d43-a8b3-4a3d144a0526
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1427706560, tx_dropped=0, tx_errors=0, tx_packets=957618}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1c21b8b6-e5db-41cc-8c9e-47fc2b9d55ba
admin_state         : down
duplex              : full
ifindex             : 1115
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

_uuid               : 8cb2002b-1010-4b14-b32c-70d30ec42715
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=2370004985, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1594124, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c12cea0e269986bb0ab75a702da760db745b8143
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Wed Apr 23 13:05:40 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Wed Apr 23 15:41:44 2014 -0700

    ofproto-dpif: Improve code clarity and comments on recirc changes to rule_dpif_lookup&#40;&#41;
    
    This patch improves the code readability and comments on the
    recirculation related changes to rule_dpif_lookup&#40;&#41; base on off-line
    discussions with Jarno.  There is no behavior changes.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
