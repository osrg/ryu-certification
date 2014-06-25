---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
817fa28a-41a3-43d8-baeb-2baa8f62a11b
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
_uuid               : 0415d1bf-a9db-445b-928e-6feef1a61846
controller          : [2d6f5e44-64e2-42cf-9702-e4620fde2097]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [02227802-f049-4dd1-990f-54d91d7ce3e5, 2c50cba3-e9b8-4fe1-9f58-4c2cedb4b7c9, 3eee4a97-2ff4-46e4-97bf-0d414dcfaa2f, 8e3ff58d-7d41-47a6-9f66-0758bd7207c5]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2d6f5e44-64e2-42cf-9702-e4620fde2097
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8e3ff58d-7d41-47a6-9f66-0758bd7207c5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4aed10eb-bc40-4c55-975e-1803320b6f9f]
name                : eth23

_uuid               : 02227802-f049-4dd1-990f-54d91d7ce3e5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [49991465-12f5-44b1-a5a7-d420d60c9bba]
name                : eth21

_uuid               : 3eee4a97-2ff4-46e4-97bf-0d414dcfaa2f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [63883769-8df0-4740-a3db-f89922eb474f]
name                : eth22

_uuid               : 2c50cba3-e9b8-4fe1-9f58-4c2cedb4b7c9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0928418e-b23c-4b17-88f3-d32199dcd1f1]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 63883769-8df0-4740-a3db-f89922eb474f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2138594208, tx_dropped=0, tx_errors=0, tx_packets=35836316}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 49991465-12f5-44b1-a5a7-d420d60c9bba
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
statistics          : {collisions=0, rx_bytes=3220913068, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=91042173, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0928418e-b23c-4b17-88f3-d32199dcd1f1
admin_state         : down
ifindex             : 688
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : 4aed10eb-bc40-4c55-975e-1803320b6f9f
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=1318688784, tx_dropped=0, tx_errors=0, tx_packets=12333056}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 5640cbd8bd18b1f7963a219ce9ae91d8a830ad5a
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Tue Jun 24 18:28:08 2014 -0700
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Wed Jun 25 08:08:11 2014 -0700

    datapath: Rehash 16-bit skbuff hashes into 32 bits.
    
    Currently, if the network stack provides skb-&gt;rxhash then we use it,
    otherwise we compute our own. However, on at least some versions of
    RHEL/CentOS, the stack provides a hash that is 16 bits rather than
    32 bits. In cases where we use the uppermost bits of the hash this
    is particularly bad because we detect that a hash is present and we
    use it rather than computing our own but the result is always zero.
    
    This is particularly noticible with tunnel ports that use the hash
    to generate a source port, such as VXLAN. On these kernels the tunnel
    source port is always the minimum value. To solve this problem while
    still taking advantage of the precomputed hash, this rehashes the
    hash so that the entropy is spread throughout 32 bits.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Thomas Graf &lt;tgraf@noironetworks.com&gt;
</pre>
