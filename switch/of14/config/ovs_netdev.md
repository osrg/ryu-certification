---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b1fc0c70-74f6-4583-aa76-85381bf5e92c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f02ee42e-438f-4b38-9fbe-cb3efe9870c0
controller          : [294f427a-80cc-47ef-90b8-d5f49f2da237]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5d43fdf6-5dc5-4712-8ee6-04c1b0723a7a, 7747429f-5f56-4775-84a2-4b1d637f5208, 8303f439-b4e4-40fb-a5d1-c90a872cab36, a1edb1ae-d9ac-462f-a38d-99c83a6c2954]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 294f427a-80cc-47ef-90b8-d5f49f2da237
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=707, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8303f439-b4e4-40fb-a5d1-c90a872cab36
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [710c6f6d-04f5-42b6-aad7-4f03efd1fe5f]
name                : eth21

_uuid               : a1edb1ae-d9ac-462f-a38d-99c83a6c2954
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [179d8a76-0469-4b64-b190-6c39b3342c64]
name                : eth23

_uuid               : 5d43fdf6-5dc5-4712-8ee6-04c1b0723a7a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4b8ab56e-a0c4-40c6-a3cc-f766ad08675e]
name                : eth22

_uuid               : 7747429f-5f56-4775-84a2-4b1d637f5208
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [248cc64d-d44f-4714-bd89-66ed1f78bb99]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 710c6f6d-04f5-42b6-aad7-4f03efd1fe5f
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
statistics          : {collisions=0, rx_bytes=794841800, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=533851, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 248cc64d-d44f-4714-bd89-66ed1f78bb99
admin_state         : down
duplex              : full
ifindex             : 39
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

_uuid               : 4b8ab56e-a0c4-40c6-a3cc-f766ad08675e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=330232892, tx_dropped=0, tx_errors=0, tx_packets=222008}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 179d8a76-0469-4b64-b190-6c39b3342c64
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=623493000, tx_dropped=0, tx_errors=0, tx_packets=415662}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f7491dce43e51c1e9e000c16dae4f86154f28d8d
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed Aug 20 02:06:04 2014 +0000
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue Aug 19 11:58:22 2014 -0700

    bfd: Clarify bfd:enable.
    
    This commit clarifies the documentation for 'bfd:enable'
    when it is not specified.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
