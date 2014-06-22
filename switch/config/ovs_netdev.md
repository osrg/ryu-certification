---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ceab9689-a613-41d2-9685-2f6e4f33e2fe
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 76ca3edd-d96f-4a9d-9b5d-87cbb5d95832
controller          : [ab7dbf01-59e1-480b-b4d9-7d98b8ede4a8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [427f9cfd-abc5-47ea-bd98-4ce6949efb3b, 96806ed8-e734-400e-9896-c33fc31c9cb7, adb0d389-d70e-45d1-8390-63bd88d0c350, b895e234-c22a-41fa-894e-59a6551eda69]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ab7dbf01-59e1-480b-b4d9-7d98b8ede4a8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=971, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b895e234-c22a-41fa-894e-59a6551eda69
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e9879b6a-5131-4e1d-9762-4a9f3ae17658]
name                : eth21

_uuid               : 96806ed8-e734-400e-9896-c33fc31c9cb7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e932bd6d-d658-4f2d-9412-fc6a6384cc1b]
name                : eth23

_uuid               : adb0d389-d70e-45d1-8390-63bd88d0c350
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0336cf02-33e7-49b0-844b-e2dae4d76f22]
name                : eth22

_uuid               : 427f9cfd-abc5-47ea-bd98-4ce6949efb3b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [608fc70b-a18a-4f72-add8-00ecc80d64cb]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e932bd6d-d658-4f2d-9412-fc6a6384cc1b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1182857080, tx_dropped=0, tx_errors=0, tx_packets=9379190}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e9879b6a-5131-4e1d-9762-4a9f3ae17658
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
statistics          : {collisions=0, rx_bytes=775348420, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=55020804, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0336cf02-33e7-49b0-844b-e2dae4d76f22
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1746737459, tx_dropped=0, tx_errors=0, tx_packets=26973839}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 608fc70b-a18a-4f72-add8-00ecc80d64cb
admin_state         : down
duplex              : full
ifindex             : 562
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
