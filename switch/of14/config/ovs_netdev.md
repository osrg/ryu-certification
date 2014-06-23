---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f13cf280-e342-4b83-8f4a-dab9eebfbc2e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b8c27740-7298-4ea9-b3c6-c7bfc953d1d6
controller          : [95697b25-bbf2-418e-9762-b9af4409ea72]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1238338d-93d8-4792-b771-d06e784c6c1c, 73bcaf21-b877-47c5-93d4-9a0b62c5ef44, 93fb9005-906f-41f3-b79e-a35f9cf4d04b, decc0208-3cfe-4218-993e-d0a16236b463]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 95697b25-bbf2-418e-9762-b9af4409ea72
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : decc0208-3cfe-4218-993e-d0a16236b463
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [283e61bd-5763-4761-b960-35384ff2815f]
name                : eth23

_uuid               : 73bcaf21-b877-47c5-93d4-9a0b62c5ef44
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [43750678-71d0-490a-a68e-4521dda4935f]
name                : br0

_uuid               : 1238338d-93d8-4792-b771-d06e784c6c1c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4450a18d-93cf-4a0f-8a7e-1a8a679081ee]
name                : eth21

_uuid               : 93fb9005-906f-41f3-b79e-a35f9cf4d04b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8b119094-ac93-493c-b82f-1558455530a0]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8b119094-ac93-493c-b82f-1558455530a0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1241656200, tx_dropped=0, tx_errors=0, tx_packets=32366959}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 43750678-71d0-490a-a68e-4521dda4935f
admin_state         : down
duplex              : full
ifindex             : 593
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

_uuid               : 4450a18d-93cf-4a0f-8a7e-1a8a679081ee
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
statistics          : {collisions=0, rx_bytes=2642670260, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=73454774, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 283e61bd-5763-4761-b960-35384ff2815f
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2324552080, tx_dropped=0, tx_errors=0, tx_packets=10140320}
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
