---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ca745d46-4602-402f-a744-955dff80ca5f
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a29be6f8-eebf-4cf6-a0da-6ae5d77550fb
controller          : [4232b684-194e-420f-9a91-c7c4f5b1bf90]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1c4f3e82-dbe9-4594-be63-14713d03163f, 245d2571-e633-4ce0-b426-e61757bb6cd2, 341e3dba-446c-4b24-a594-079fa7e64764, 5ef7027f-a496-433c-b707-edeb26ebcfee]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4232b684-194e-420f-9a91-c7c4f5b1bf90
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=852, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 245d2571-e633-4ce0-b426-e61757bb6cd2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bffd5bfc-cf82-499b-a8bf-019b652d58c9]
name                : eth23

_uuid               : 341e3dba-446c-4b24-a594-079fa7e64764
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c819248c-bfa4-49fc-bca9-3f948c607755]
name                : eth21

_uuid               : 1c4f3e82-dbe9-4594-be63-14713d03163f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cf7e4e48-2fc2-4e5c-8819-f1ca0cee7c8a]
name                : br0

_uuid               : 5ef7027f-a496-433c-b707-edeb26ebcfee
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bb4fc532-0f6f-426e-9164-f0850848c25d]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c819248c-bfa4-49fc-bca9-3f948c607755
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
statistics          : {collisions=0, rx_bytes=271338612923, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=181004613, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bffd5bfc-cf82-499b-a8bf-019b652d58c9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=14556990000, tx_dropped=0, tx_errors=0, tx_packets=9704660}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : cf7e4e48-2fc2-4e5c-8819-f1ca0cee7c8a
admin_state         : down
duplex              : full
ifindex             : 327
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

_uuid               : bb4fc532-0f6f-426e-9164-f0850848c25d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=160831249392, tx_dropped=0, tx_errors=0, tx_packets=107271464}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5167d6b010082d0a164fd743800fe653bbb310d2
Author:     Eitan Eliahu &lt;eliahue@vmware.com&gt;
AuthorDate: Wed Nov 5 01:39:20 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Nov 5 07:28:23 2014 -0800

    router-table-stub: Fix compilation error.
    
    Signed-off-by: Eitan Eliahu &lt;eliahue@vmware.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
