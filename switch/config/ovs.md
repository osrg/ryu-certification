---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
49546dc9-30cc-4352-af68-e334729fb05b
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
_uuid               : 0d4587e6-dac9-4f14-abc5-271d01ce4c64
controller          : [c83b1c7f-4b7f-4c18-a862-dac038fb1e87]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6abed006-8b4b-40a7-a863-fc6743d800b1, c99b32c7-56bb-4603-bf83-e34c686bb3c9, d1ed2963-5ad7-487c-9fe9-e00213e0a4c1]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c83b1c7f-4b7f-4c18-a862-dac038fb1e87
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=357, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6abed006-8b4b-40a7-a863-fc6743d800b1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e70e3577-9e9e-44a5-8c39-2aa9254348ab]
name                : eth7

_uuid               : d1ed2963-5ad7-487c-9fe9-e00213e0a4c1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [25b40cb7-de87-4108-9129-0a0b14a91997]
name                : br0

_uuid               : c99b32c7-56bb-4603-bf83-e34c686bb3c9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [552f077f-efe1-46cc-9be5-da686fb46e01]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e70e3577-9e9e-44a5-8c39-2aa9254348ab
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

_uuid               : 552f077f-efe1-46cc-9be5-da686fb46e01
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

_uuid               : 25b40cb7-de87-4108-9129-0a0b14a91997
admin_state         : up
ifindex             : 129
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
