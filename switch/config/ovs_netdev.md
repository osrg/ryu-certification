---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cbb5847a-4bd3-4cff-90e3-835fd034d273
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
_uuid               : 6df01dcd-20f7-4634-9d22-3469fed6817a
controller          : [3742b645-1b8d-4487-9e44-99066f3935c5]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [002b6ba8-9215-45a1-8d4a-8ebd94751bec, 897b0967-ff7f-4996-b699-c13d33d43768, ad6e07f2-bdc5-4a88-bebb-10bdcee566c7, bdb11aa0-bbf6-4b6b-abe2-870838c0e418]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3742b645-1b8d-4487-9e44-99066f3935c5
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=572, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bdb11aa0-bbf6-4b6b-abe2-870838c0e418
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [34f5ef47-8406-4988-a184-032a26c4e939]
name                : br0

_uuid               : 002b6ba8-9215-45a1-8d4a-8ebd94751bec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cb8a7ddb-82be-4883-b6ed-50eaadf75755]
name                : eth22

_uuid               : ad6e07f2-bdc5-4a88-bebb-10bdcee566c7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ec2eaeab-330f-4267-b952-785a96f747eb]
name                : eth23

_uuid               : 897b0967-ff7f-4996-b699-c13d33d43768
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ec93ea9c-8721-4626-83fa-e1fe5e2aaef5]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ec93ea9c-8721-4626-83fa-e1fe5e2aaef5
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
statistics          : {collisions=0, rx_bytes=632374861, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=430973, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : cb8a7ddb-82be-4883-b6ed-50eaadf75755
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=404625115, tx_dropped=0, tx_errors=0, tx_packets=273674}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 34f5ef47-8406-4988-a184-032a26c4e939
admin_state         : down
duplex              : full
ifindex             : 1074
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

_uuid               : ec2eaeab-330f-4267-b952-785a96f747eb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=344173500, tx_dropped=0, tx_errors=0, tx_packets=229449}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
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
