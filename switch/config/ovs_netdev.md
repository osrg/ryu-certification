---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f616375d-f835-4de8-8c22-ddd32b0e67ef
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f9c35f9f-495b-446d-abfd-55fdd365a511
controller          : [13950b57-dd32-44ac-be5e-ace39f4a9193]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0d27b31a-3c1d-435f-abfd-b00bb5edf192, 6c37a9a8-e9bb-4269-ad49-f8da9d384570, a17d55fb-8105-45cd-bcde-0e401e766b4b, ab801f75-ea25-4f7c-b93c-4eef5c88d5db]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 13950b57-dd32-44ac-be5e-ace39f4a9193
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=556, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6c37a9a8-e9bb-4269-ad49-f8da9d384570
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9f602338-3449-4a59-84ad-f65f1ef018e8]
name                : eth23

_uuid               : ab801f75-ea25-4f7c-b93c-4eef5c88d5db
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [85b04fcb-8f5c-4f4d-8001-d0838f38fd1e]
name                : eth22

_uuid               : 0d27b31a-3c1d-435f-abfd-b00bb5edf192
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fe479aaa-a245-468a-9a1e-1ceee0f7e94c]
name                : eth21

_uuid               : a17d55fb-8105-45cd-bcde-0e401e766b4b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [56a41349-62bc-4015-9f04-72aada790e31]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9f602338-3449-4a59-84ad-f65f1ef018e8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1455585000, tx_dropped=0, tx_errors=0, tx_packets=970390}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 56a41349-62bc-4015-9f04-72aada790e31
admin_state         : down
duplex              : full
ifindex             : 81
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

_uuid               : fe479aaa-a245-468a-9a1e-1ceee0f7e94c
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
statistics          : {collisions=0, rx_bytes=1916699355, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1283211, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 85b04fcb-8f5c-4f4d-8001-d0838f38fd1e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=671336608, tx_dropped=0, tx_errors=0, tx_packets=449567}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 682800a4ef8238383443a11b14272b3ed448ebe3
Author:     Flavio Leitner &lt;fbl@redhat.com&gt;
AuthorDate: Fri Apr 11 18:34:15 2014 -0300
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon May 19 15:57:25 2014 -0700

    ofproto-dpif-xlate: Add xlate_normal_flood&#40;&#41;
    
    This is also needed for multicast snooping.
    
    Acked-by: Thomas Graf &lt;tgraf@redhat.com&gt;
    Acked-by: Daniel Borkmann &lt;dborkman@redhat.com&gt;
    Signed-off-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
