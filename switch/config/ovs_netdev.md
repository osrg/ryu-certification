---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
84a0f11c-da39-4ba6-9201-4520dc3ff029
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
_uuid               : 37bda5c5-ecc2-40c9-acdd-1207f44e4d62
controller          : [771afe13-1ee6-4f7e-8fd7-a358abe1e4dc]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [06c1f163-043b-41c9-bfd3-f0a34acd4b3a, 1656a1e0-2419-488f-8749-b363eb8f38cc, 80a8bd62-7770-4b03-952b-7db70ce5d7fa]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 771afe13-1ee6-4f7e-8fd7-a358abe1e4dc
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=302, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1656a1e0-2419-488f-8749-b363eb8f38cc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [391410fa-caed-4f83-9b38-4cde0701eb78]
name                : eth8

_uuid               : 80a8bd62-7770-4b03-952b-7db70ce5d7fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [92e49bc6-1bb7-4d79-996a-f1a2dd7d4021]
name                : eth7

_uuid               : 06c1f163-043b-41c9-bfd3-f0a34acd4b3a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c21c17b4-53d5-4f41-93d9-7024554700f3]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c21c17b4-53d5-4f41-93d9-7024554700f3
admin_state         : up
duplex              : full
ifindex             : 118
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 92e49bc6-1bb7-4d79-996a-f1a2dd7d4021
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
statistics          : {collisions=0, rx_bytes=3053777972, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72539278, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 391410fa-caed-4f83-9b38-4cde0701eb78
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=754838, tx_dropped=0, tx_errors=0, tx_packets=8068}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a66034810666e84377e167ad88ea961caa8b4d17
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Fri Jan 31 15:47:58 2014 -0800
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Fri Jan 31 19:09:45 2014 -0800

    datapth: Suppress error messages on megaflow updates
    
    With subfacets, we'd expect megaflow updates message to carry
    the original micro flow. If not, EINVAL is returned and kernel
    logs an error message.  Now that the user space subfacet layer is
    removed, it is expected that flow updates can arrive with a
    micro flow other than the original. Change the return code to
    EEXIST and remove the kernel error log message.
    
    Reported-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
