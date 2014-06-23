---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
619bc89e-1c09-4f5a-be66-fb33e8fbaf2c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 36b12721-e9a4-4c28-9ac7-ae19138f0322
controller          : [d1d10fbd-7937-4431-88fe-413b258017b8]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [29621dde-5c23-4e3b-a71f-b9860fff2280, 92ebf553-386e-40f3-a836-1e8eaea0c117, e61d7f2c-68f1-4043-a6af-abb38cdd4f1b, f8515856-626c-4745-ad40-903be0cde84c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : d1d10fbd-7937-4431-88fe-413b258017b8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e61d7f2c-68f1-4043-a6af-abb38cdd4f1b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f8bc3a33-80d7-4a9d-a41f-c8efd3b0281c]
name                : eth22

_uuid               : f8515856-626c-4745-ad40-903be0cde84c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e551618b-222b-4fca-9c6f-12b19c7a75b4]
name                : eth23

_uuid               : 29621dde-5c23-4e3b-a71f-b9860fff2280
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2fe9a286-708d-47f0-9f11-22910f3c5b2e]
name                : br0

_uuid               : 92ebf553-386e-40f3-a836-1e8eaea0c117
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6822177f-b8bc-4001-91bb-b99f4db2b3e6]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2fe9a286-708d-47f0-9f11-22910f3c5b2e
admin_state         : down
ifindex             : 568
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

_uuid               : e551618b-222b-4fca-9c6f-12b19c7a75b4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1282025080, tx_dropped=0, tx_errors=0, tx_packets=9445302}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6822177f-b8bc-4001-91bb-b99f4db2b3e6
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
statistics          : {collisions=0, rx_bytes=892251767, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=55099374, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f8bc3a33-80d7-4a9d-a41f-c8efd3b0281c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1787835051, tx_dropped=0, tx_errors=0, tx_packets=27001472}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8faeab7257a28ccf3a13d2e823cef83feabbb44c
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Mon Jun 23 04:39:47 2014 +0000
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Mon Jun 23 09:44:16 2014 +1200

    Makefile.am: fix printf-check in out-of-tree build
    
    The introduction of a %zu in datapath/flow_netlink.c with commit c1fc1411
    revealed a problem with out-of-tree builds.
    
    printf-check and thread-safety-check skip some directories with a 'grep -v'.
    In the case of an out-of-tree build, the grep -v pattern doesn't work, because
    it assumes the pathnames to be relative to the OVS root directory.
    
    This commit fixes the problem by changing the directory before executing any
    commands, like we do elsewhere in Makefile.am
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
