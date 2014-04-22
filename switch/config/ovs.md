---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cf28e9a3-e104-42cf-bcf2-c2084c324311
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : fa5e9e05-b377-4f54-beac-a7c54a285cf9
controller          : [d781cf45-cccb-4f34-a392-4c3fd4b7dc27]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4c3ac5a1-ad13-45d7-bd71-dcac814d91f6, 59eadfed-b57d-4cff-a417-ad9ae528c2dd, 6d05e919-cb02-4698-b570-4a1bd00758b1, 9fd7139a-851c-4e8f-91c8-0f79c0024e3f]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d781cf45-cccb-4f34-a392-4c3fd4b7dc27
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=10, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 59eadfed-b57d-4cff-a417-ad9ae528c2dd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [284500ff-44e6-4be1-8c60-07f8092fd7d8]
name                : eth22

_uuid               : 4c3ac5a1-ad13-45d7-bd71-dcac814d91f6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e054232c-747c-429d-a7a4-44ff9d63749d]
name                : eth23

_uuid               : 6d05e919-cb02-4698-b570-4a1bd00758b1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [596161f3-6539-4279-bc77-57e48b62e64c]
name                : br0

_uuid               : 9fd7139a-851c-4e8f-91c8-0f79c0024e3f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e5627a0e-e624-4dc9-83d1-82f7de483b90]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e054232c-747c-429d-a7a4-44ff9d63749d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e5627a0e-e624-4dc9-83d1-82f7de483b90
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
statistics          : {collisions=0, rx_bytes=57236, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=620, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 284500ff-44e6-4be1-8c60-07f8092fd7d8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18550, tx_dropped=0, tx_errors=0, tx_packets=198}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 596161f3-6539-4279-bc77-57e48b62e64c
admin_state         : down
ifindex             : 1079
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3aadc5bbb058d52bb350424cbfef80f2d0c50ecd
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Mon Apr 21 20:05:08 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Mon Apr 21 21:14:04 2014 -0700

    ofproto-dpif-upcall: Fix logic error in handler/revalidator threads
    creation and deletion.
    
    Commit 1f8675481e &#40;ofproto-dpif-upcall: Fix ovs-vswitchd crash.&#41;
    directly copied the udpif_set_threads&#40;&#41; logic to udpif_stop_threads&#40;&#41;
    and udpif_start_threads&#40;&#41;.  In fact, this was erroneous and caused
    unittest failures.
    
    This commit fixes the above issue by correcting the checks in
    udpif_stop_threads&#40;&#41; and udpif_start_threads&#40;&#41;, and adding necessary
    checks in udpif_set_threads&#40;&#41;.
    
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
