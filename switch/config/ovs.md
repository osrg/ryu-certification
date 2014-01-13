---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1c1440a6-a0ff-4428-8def-e25aec89c1d7
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b657db32-a5fe-4b04-930a-c64d08b4263d
controller          : [a331c100-7fde-428b-b43a-c7752203fdbe]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3de6c9c7-f7b9-4f5a-b9e2-a2c3742c6a32, 49e84912-e550-4795-9c31-0bf63ca04e1b, cffcb124-4e92-42d8-8a0f-4594b2517815]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a331c100-7fde-428b-b43a-c7752203fdbe
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : cffcb124-4e92-42d8-8a0f-4594b2517815
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [843f3c6d-d6b2-4540-9cfd-effd4d8b72b5]
name                : eth7

_uuid               : 49e84912-e550-4795-9c31-0bf63ca04e1b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [11502e8b-a167-4d8c-aa64-0ee679ae7563]
name                : eth8

_uuid               : 3de6c9c7-f7b9-4f5a-b9e2-a2c3742c6a32
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [46182e89-aa62-47ee-97a9-b9fc7790f3ba]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 46182e89-aa62-47ee-97a9-b9fc7790f3ba
admin_state         : up
ifindex             : 55
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

_uuid               : 843f3c6d-d6b2-4540-9cfd-effd4d8b72b5
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

_uuid               : 11502e8b-a167-4d8c-aa64-0ee679ae7563
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2e275c0e00adced5dab256e5ccd1b4ae60ec127d
Author:     Francesco Fusco &lt;ffusco@redhat.com&gt;
AuthorDate: Thu Dec 19 18:16:24 2013 +0100
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Jan 13 13:25:57 2014 -0800

    sFlow: clear the padding
    
    putString pads the string to the 4-byte boundary without
    clearing the padded memory. This patch simply set the
    padding to zero.
    
    Signed-off-by: Francesco Fusco &lt;ffusco@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
