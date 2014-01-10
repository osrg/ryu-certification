---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
00d1c4a5-33b1-4e35-bf2f-4bb497b7a7c8
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8a0d946f-c8a1-4d19-9042-95ee60ad9f3d
controller          : [a363614c-5f4a-4bee-99b7-f27bd6b075c4]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0070fb4d-2c80-4542-8512-021f46e74a4b, 2bb9f769-071c-4848-983d-0e30bf29b3ee, dcbe7c28-dc3d-4de5-83ea-1e20febaf697]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a363614c-5f4a-4bee-99b7-f27bd6b075c4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : dcbe7c28-dc3d-4de5-83ea-1e20febaf697
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1a85d7f2-d62b-4df0-a74e-b3a13764b615]
name                : br0

_uuid               : 2bb9f769-071c-4848-983d-0e30bf29b3ee
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [92df2e6b-df66-404e-b4ee-77efa67c9c10]
name                : eth8

_uuid               : 0070fb4d-2c80-4542-8512-021f46e74a4b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4ae05273-fe29-447d-81fa-fa925c5fc004]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1a85d7f2-d62b-4df0-a74e-b3a13764b615
admin_state         : up
ifindex             : 37
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

_uuid               : 92df2e6b-df66-404e-b4ee-77efa67c9c10
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

_uuid               : 4ae05273-fe29-447d-81fa-fa925c5fc004
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit deb64473f677e81f6a63db9c35de501c438e1342
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Dec 31 14:23:34 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jan 10 10:52:51 2014 -0800

    Update build requirements.
    
    Libtool is now required as of commit 38b7a52b61 (openvswitch: Use libtool
    and allow building shared libs).
    
    It seems that a build requirement for Python slipped in a while back, for
    generating ovs-vswitchd.conf.db.5, and no one complained, so we might as
    well make it official.  (That will let us simplify some bits of the build,
    too, since they won't have to be conditional on Python anymore, so I'm all
    in favor of this change.)
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
