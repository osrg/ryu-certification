---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e5790334-57e0-4f3a-8659-8db974750dc1
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
_uuid               : bb70b309-44e0-4e69-8ec4-e048153d052b
controller          : [163bc188-4bba-480a-affb-2eebcdf611a4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0f8d0023-60d4-46aa-acb4-f215f6818f0e, 2844fb99-9b0f-4927-b858-51859fc05008, 42189e1f-4953-4242-bd6f-32426936e8c7, 73f494af-771e-4b0a-8313-26c3defa1b40]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 163bc188-4bba-480a-affb-2eebcdf611a4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=552, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2844fb99-9b0f-4927-b858-51859fc05008
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [901f6129-e9e0-4791-8a9d-7225b8ef909e]
name                : eth23

_uuid               : 0f8d0023-60d4-46aa-acb4-f215f6818f0e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4f07a19f-96a6-4f97-aae8-9467dbd06e2e]
name                : br0

_uuid               : 73f494af-771e-4b0a-8313-26c3defa1b40
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [593e01e0-5276-4b3c-acce-0199da23e33d]
name                : eth22

_uuid               : 42189e1f-4953-4242-bd6f-32426936e8c7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ad42efda-1bdc-42cb-b409-27fa942e458d]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 593e01e0-5276-4b3c-acce-0199da23e33d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2320445884, tx_dropped=0, tx_errors=0, tx_packets=1554268}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 901f6129-e9e0-4791-8a9d-7225b8ef909e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4013569500, tx_dropped=0, tx_errors=0, tx_packets=2675713}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ad42efda-1bdc-42cb-b409-27fa942e458d
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
statistics          : {collisions=0, rx_bytes=1361720081, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=3790640, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4f07a19f-96a6-4f97-aae8-9467dbd06e2e
admin_state         : down
duplex              : full
ifindex             : 200
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
commit 3b3f885732a8cc7424812dd65be0ed8755b70438
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Thu May 22 19:15:26 2014 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri May 23 09:19:25 2014 -0700

    makefile.am: Apply printf check only to OVS userspace.
    
    We shouldn't restrict printf specifiers in kernel or third party
    code.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
