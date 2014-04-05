---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f7294c78-b314-4efa-afd9-133237b3ba08
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b1dce75c-13f6-4412-9ddc-21e062bb7d91
controller          : [73c03d33-92ac-4f78-920c-9c57dfcae151]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0bcaabfc-225d-4377-b20a-16bdc1f3cf7c, 1dd2333e-90c7-4632-a92c-afbd607eb24b, 543f2a90-066f-4888-aa29-d99e647ad27c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 73c03d33-92ac-4f78-920c-9c57dfcae151
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=927, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0bcaabfc-225d-4377-b20a-16bdc1f3cf7c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [16eee009-8de8-46df-8539-7c432392d9c5]
name                : br0

_uuid               : 543f2a90-066f-4888-aa29-d99e647ad27c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dd690362-a3a9-4fec-aaf7-3b3fa0b38909]
name                : eth7

_uuid               : 1dd2333e-90c7-4632-a92c-afbd607eb24b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b8c96407-1c1b-4323-917a-69e471ed9742]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 16eee009-8de8-46df-8539-7c432392d9c5
admin_state         : down
duplex              : full
ifindex             : 895
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : dd690362-a3a9-4fec-aaf7-3b3fa0b38909
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
statistics          : {collisions=0, rx_bytes=3073734540, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72741513, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : b8c96407-1c1b-4323-917a-69e471ed9742
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6807395, tx_dropped=0, tx_errors=0, tx_packets=72563}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit dea241f172b64958f6b917bc3971253c5dc010c0
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Apr 4 19:26:22 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Sat Apr 5 10:46:26 2014 -0700

    ofp-print: Fix misaligned data access in ofp_print_error_msg().
    
    The body of an OpenFlow error message often contains an inner OpenFlow
    message, and when it does, the inner message starts at an odd multiple of 4
    bytes from the beginning of the outer message.  That means that, on RISC
    systems, accessing the inner message directly causes a bus error.  This
    commit fixes the problem in a way that should make it difficult to recur.
    
    This fixes the failure of tests 643, 645, and 651 on sparc seen here:
    https://buildd.debian.org/status/fetch.php?pkg=openvswitch&amp;arch=sparc&amp;ver=2.1.0%2Bgit20140325-1&amp;stamp=1396438624
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
