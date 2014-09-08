---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7a353511-c436-471c-8e32-80eb8f16d15e
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
_uuid               : 06723dc8-4b09-42b6-bbbf-550dee099901
controller          : [76e7c9ea-69b6-46cb-964d-5fe575d24225]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [059bfb1f-9b66-456c-8c88-04ce0a9233f7, 1c50faac-6837-45d1-9bc9-da249c07c137, c14dcee1-3e14-4812-a870-a4df4c3ceca7, cb46e2e3-a64d-4991-860d-293808735471]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 76e7c9ea-69b6-46cb-964d-5fe575d24225
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=702, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1c50faac-6837-45d1-9bc9-da249c07c137
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [037f41ac-92ad-4531-a341-4af2401e517d]
name                : eth23

_uuid               : c14dcee1-3e14-4812-a870-a4df4c3ceca7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d7f119da-f8c4-44f4-ac83-7030747a5f55]
name                : eth22

_uuid               : 059bfb1f-9b66-456c-8c88-04ce0a9233f7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c3a0e95d-5294-45aa-86cd-449027556780]
name                : eth21

_uuid               : cb46e2e3-a64d-4991-860d-293808735471
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [78a55b42-e519-4b5c-925b-3f927b1f548f]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 037f41ac-92ad-4531-a341-4af2401e517d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4255183500, tx_dropped=0, tx_errors=0, tx_packets=2836789}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c3a0e95d-5294-45aa-86cd-449027556780
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
statistics          : {collisions=0, rx_bytes=3254593174, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=56603995, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 78a55b42-e519-4b5c-925b-3f927b1f548f
admin_state         : down
duplex              : full
ifindex             : 110
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

_uuid               : d7f119da-f8c4-44f4-ac83-7030747a5f55
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3645743386, tx_dropped=0, tx_errors=0, tx_packets=39667663}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3d76b86c6f0b56ee8649356c49e89dd5022451b2
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Mon Sep 8 10:41:36 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Mon Sep 8 13:07:07 2014 -0700

    ofproto-dpif-upcall: Fix a free of uninitialized memory.
    
    On current master, when 'upcall_receive&#40;&#41;' returns error, the
    ofpbuf 'upcall-&gt;put_actions' is uninitialized.  In some usecase,
    the failure of 'upcall_receive&#40;&#41;' will cause uninitialize of
    'upcall-&gt;put_actions' and free of uninitialized pointer.
    
    This commit fixes the issue by making the caller not conduct
    the uninitialize of the 'upcall' when there is error.
    
    Found by inspection.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
