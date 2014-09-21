---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f5230897-a00d-4c88-a511-82fdecdd39cf
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : cc534072-de70-4aa2-862b-349b3c663580
controller          : [4439636c-7165-4f58-b23b-c045ebbf6120]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2ee7f11d-9ab1-4092-9d48-743592bbba6c, 8e210031-5874-49cd-b9df-24062b413da8, d2bf970c-6e24-4347-b7f3-2e56350035f7, f04dc6e9-2b45-42e1-b96e-c71eb0b09d8e]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4439636c-7165-4f58-b23b-c045ebbf6120
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=706, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d2bf970c-6e24-4347-b7f3-2e56350035f7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ebb80916-911c-4aaf-86c8-f87ec164398c]
name                : eth23

_uuid               : 8e210031-5874-49cd-b9df-24062b413da8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7e7e83a4-7114-4275-8ae6-5a0b1f535845]
name                : eth22

_uuid               : f04dc6e9-2b45-42e1-b96e-c71eb0b09d8e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [43a9ae46-123b-4891-825a-6ac6868b2630]
name                : eth21

_uuid               : 2ee7f11d-9ab1-4092-9d48-743592bbba6c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e39a47d8-1afe-4efc-8db4-37a8b246ad2c]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7e7e83a4-7114-4275-8ae6-5a0b1f535845
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2129438470, tx_dropped=0, tx_errors=0, tx_packets=47254850}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e39a47d8-1afe-4efc-8db4-37a8b246ad2c
admin_state         : down
duplex              : full
ifindex             : 160
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

_uuid               : ebb80916-911c-4aaf-86c8-f87ec164398c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2287977704, tx_dropped=0, tx_errors=0, tx_packets=4388630}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 43a9ae46-123b-4891-825a-6ac6868b2630
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
statistics          : {collisions=0, rx_bytes=4224868729, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74448666, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e74d48171e590b50cdcb2798a3e7c5c32313887b
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Wed Sep 17 18:58:44 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Sat Sep 20 19:45:56 2014 -0700

    datapath: Remove pkt_key from OVS_CB.
    
    OVS keeps pointer to packet key in skb-&gt;cb, but the packet key is
    store on stack. This could make code bit tricky. So it is better to
    get rid of the pointer.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
