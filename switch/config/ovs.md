---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b6841705-520a-4676-a31b-eee5805d49fd
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8cdc0266-b37d-4e9c-bde9-d26e06b2dd21
controller          : [b8c723ba-dc2f-4903-9843-a19705e3fdc1]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2b0c363a-a076-47c2-807b-e504ea5d8323, 61fb37e2-f641-4cea-ae4e-5a6040a87437, 995b5fc9-e0ff-40b9-8088-ba9f9c758d5a, a703e301-68e1-4185-80bc-d5cee15ed209]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b8c723ba-dc2f-4903-9843-a19705e3fdc1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=20, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a703e301-68e1-4185-80bc-d5cee15ed209
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1ca098f4-f79b-47c1-8a71-768a088c235f]
name                : eth23

_uuid               : 995b5fc9-e0ff-40b9-8088-ba9f9c758d5a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d6f91ebd-f5c4-4621-861f-9949acda3d95]
name                : br0

_uuid               : 61fb37e2-f641-4cea-ae4e-5a6040a87437
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd128b2d-052d-4e7c-bd95-9ad4fe5c2fbe]
name                : eth22

_uuid               : 2b0c363a-a076-47c2-807b-e504ea5d8323
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d186345f-c9af-4206-870c-364a653adc96]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1ca098f4-f79b-47c1-8a71-768a088c235f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1110759704, tx_dropped=0, tx_errors=0, tx_packets=3603818}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d6f91ebd-f5c4-4621-861f-9949acda3d95
admin_state         : down
ifindex             : 250
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : cd128b2d-052d-4e7c-bd95-9ad4fe5c2fbe
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2984926990, tx_dropped=0, tx_errors=0, tx_packets=2001166}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d186345f-c9af-4206-870c-364a653adc96
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
statistics          : {collisions=0, rx_bytes=3114913060, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=4970150, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
