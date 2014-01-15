---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
36f5e3d9-f2a6-4527-9201-185ae354406c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 25843e89-2016-4604-996b-d89174105392
controller          : [32d018fe-2e6a-435e-9ed8-13badb464414]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0e35003b-5bc5-44a8-a389-42db000f136e, bd70ea5f-d1ca-4ddd-9d37-18195096d0f1, e5e0c09d-07b1-4f5b-91b6-9b76c66d8ccd]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 32d018fe-2e6a-435e-9ed8-13badb464414
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e5e0c09d-07b1-4f5b-91b6-9b76c66d8ccd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f427f441-7a74-4cde-9225-34633d07cff8]
name                : eth8

_uuid               : bd70ea5f-d1ca-4ddd-9d37-18195096d0f1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9f720d95-e309-4d96-8a33-5737614bcee7]
name                : br0

_uuid               : 0e35003b-5bc5-44a8-a389-42db000f136e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2c5adc8e-77b0-4d0c-a228-d29bda266023]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f427f441-7a74-4cde-9225-34633d07cff8
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

_uuid               : 9f720d95-e309-4d96-8a33-5737614bcee7
admin_state         : up
ifindex             : 79
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

_uuid               : 2c5adc8e-77b0-4d0c-a228-d29bda266023
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
commit ef507cecc926a3f42bb59de1b2aff6f119838c6a
Author:     Thomas Graf &lt;tgraf@suug.ch&gt;
AuthorDate: Tue Jan 14 01:27:02 2014 -0800
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Tue Jan 14 01:27:02 2014 -0800

    datapath: Pad OVS_PACKET_ATTR_PACKET if linear copy was performed
    
    While the zerocopy method is correctly omitted if user space
    does not support unaligned Netlink messages. The attribute is
    still not padded correctly as skb_zerocopy() will not ensure
    padding and the attribute size is no longer pre calculated
    though nla_reserve() which ensured padding previously.
    
    This patch applies appropriate padding if a linear data copy
    was performed in skb_zerocopy().
    
    Signed-off-by: Thomas Graf &lt;tgraf@suug.ch&gt;
    Acked-by: Zoltan Kiss &lt;zoltan.kiss@citrix.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
