---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a258396d-566c-40f5-a4ef-98489c33ab5d
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
_uuid               : b5b9dac6-ab4b-4f80-a9c7-a31d32021f18
controller          : [e5cb2679-4b5d-4b50-b800-83e534534436]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4a21064f-6646-4b48-952d-f4ada49be63c, a967f3ec-bfbd-4f92-bafa-db018db669dc, fda90f86-05bf-4927-8f24-82e86cffb02b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e5cb2679-4b5d-4b50-b800-83e534534436
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a967f3ec-bfbd-4f92-bafa-db018db669dc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a40b404-2e17-4d9f-bbad-3992109bc661]
name                : eth8

_uuid               : fda90f86-05bf-4927-8f24-82e86cffb02b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bcda5ec0-7d4b-407f-b178-7a8c9f7f29b0]
name                : eth7

_uuid               : 4a21064f-6646-4b48-952d-f4ada49be63c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b1c2171f-9f4c-4c1a-ae0a-3e9b22821990]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0a40b404-2e17-4d9f-bbad-3992109bc661
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1038584, tx_dropped=0, tx_errors=0, tx_packets=11162}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : bcda5ec0-7d4b-407f-b178-7a8c9f7f29b0
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
statistics          : {collisions=0, rx_bytes=2336306250, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1588362, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : b1c2171f-9f4c-4c1a-ae0a-3e9b22821990
admin_state         : up
duplex              : full
ifindex             : 127
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 64ca9472f0b0f40b94abe2adf5d397bdf3d5e7b3
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Wed Jan 22 06:50:49 2014 +0000
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Tue Jan 21 15:39:31 2014 -0800

    upcall: Cache the number of flows from the datapath.
    
    Fetching the number of flows in the datapath has been causing
    unnecessary contention on the kernel ovs_lock in recent TCP CRR tests.
    This patch caches this number for up to 100ms in the userspace to reduce
    such kernel calls.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Co-authored-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off--by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
