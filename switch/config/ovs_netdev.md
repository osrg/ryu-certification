---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
27ca2a13-a165-40b2-8f99-945d28c33ee0
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 89a10c47-5da4-4072-bf35-376b54d2d519
controller          : [fbe6279f-636e-48f6-af0d-e720bfa824f5]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [121dc1e0-31e5-4fc8-a030-4bdf72ca0d70, 9304dc58-ce37-4c79-9086-f97d59a99df4, a3d2494d-968f-4734-9d43-b5d8f262780d, a73e00e1-3ce3-4537-a7ea-8accf6fc44a3]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fbe6279f-636e-48f6-af0d-e720bfa824f5
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=997, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 121dc1e0-31e5-4fc8-a030-4bdf72ca0d70
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [651438cf-97a8-47ac-928b-5ce440b6b2d3]
name                : eth21

_uuid               : 9304dc58-ce37-4c79-9086-f97d59a99df4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [02a7f4c4-8f30-4af7-a8c5-2b65c448f34b]
name                : eth23

_uuid               : a3d2494d-968f-4734-9d43-b5d8f262780d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e42b1528-db0c-403c-98bf-bc7e853dd2d0]
name                : eth22

_uuid               : a73e00e1-3ce3-4537-a7ea-8accf6fc44a3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [70b594f8-422f-44ad-98b8-0944118ce5a1]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 70b594f8-422f-44ad-98b8-0944118ce5a1
admin_state         : down
duplex              : full
ifindex             : 246
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

_uuid               : e42b1528-db0c-403c-98bf-bc7e853dd2d0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2903104586, tx_dropped=0, tx_errors=0, tx_packets=1946246}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 02a7f4c4-8f30-4af7-a8c5-2b65c448f34b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=912143204, tx_dropped=0, tx_errors=0, tx_packets=3471407}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 651438cf-97a8-47ac-928b-5ce440b6b2d3
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
statistics          : {collisions=0, rx_bytes=2881181500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=4813150, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 84f0f298298465f9bd6f7e794b671587e4556503
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Tue May 27 17:34:14 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue May 27 17:41:19 2014 -0700

    ofproto-dpif-xlate: Implement RCU locking in ofproto-dpif-xlate.
    
    Before, a global read-write lock protected the ofproto-dpif
    / ofproto-dpif-xlate interface.  Handler and revalidator threads
    had to wait while configuration was being changed.  This patch
    implements RCU locking which allows handlers and revalidators
    to operate while configuration is being updated.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
