---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d557263e-9cc0-45c0-88c6-09146755f17a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b451ef4a-b422-420c-838f-c689854d408b
controller          : [75848d8a-dff9-4098-a20b-bcf7bba32275]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0126f2b5-1199-48de-8c8b-e78feaa9199c, 23f9cbee-9df5-4ad8-8382-de5d2f02c5a3, abba1600-a9a9-4a89-8edc-4f41e817858f, dca179dc-fd89-490f-837d-18d37b19afdc]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 75848d8a-dff9-4098-a20b-bcf7bba32275
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=992, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : dca179dc-fd89-490f-837d-18d37b19afdc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [67d867e7-f22c-4b69-8213-6e7833e88200]
name                : br0

_uuid               : abba1600-a9a9-4a89-8edc-4f41e817858f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5e2b44cd-afeb-4127-94d1-122e44df7511]
name                : eth22

_uuid               : 0126f2b5-1199-48de-8c8b-e78feaa9199c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1c7730c4-ab78-487d-9a76-cc9dca9da73a]
name                : eth23

_uuid               : 23f9cbee-9df5-4ad8-8382-de5d2f02c5a3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c28e9089-589d-4660-a019-09aaf83ed8c2]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 1c7730c4-ab78-487d-9a76-cc9dca9da73a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1778739580, tx_dropped=0, tx_errors=0, tx_packets=9776445}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5e2b44cd-afeb-4127-94d1-122e44df7511
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1992385801, tx_dropped=0, tx_errors=0, tx_packets=27138940}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c28e9089-589d-4660-a019-09aaf83ed8c2
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
statistics          : {collisions=0, rx_bytes=1476725933, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=55492145, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 67d867e7-f22c-4b69-8213-6e7833e88200
admin_state         : down
duplex              : full
ifindex             : 582
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
