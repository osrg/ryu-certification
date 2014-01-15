---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
199c75a6-65c3-474e-8380-c596992b227e
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
_uuid               : 79090623-3dcf-416c-93ca-83f248f05b8b
controller          : [db9e7d8a-4018-47c5-a50d-470ed885ba7f]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [96dbe6c2-0683-46e9-b68a-5af89df55462, c042c1ce-0941-4528-95ee-731a54f0bd78, ce399e8a-830b-4f8d-a0c9-354c683d1e36]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : db9e7d8a-4018-47c5-a50d-470ed885ba7f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=296, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 96dbe6c2-0683-46e9-b68a-5af89df55462
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc413dc7-e5bf-49b8-9852-9247bd41acb7]
name                : br0

_uuid               : ce399e8a-830b-4f8d-a0c9-354c683d1e36
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1c7c9be9-f048-4454-a750-7935d3491435]
name                : eth7

_uuid               : c042c1ce-0941-4528-95ee-731a54f0bd78
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e80263f4-190d-4681-8089-d20fdf11bf12]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e80263f4-190d-4681-8089-d20fdf11bf12
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=510436, tx_dropped=0, tx_errors=0, tx_packets=5500}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 1c7c9be9-f048-4454-a750-7935d3491435
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
statistics          : {collisions=0, rx_bytes=1631625, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16500, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : bc413dc7-e5bf-49b8-9852-9247bd41acb7
admin_state         : up
duplex              : full
ifindex             : 77
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
