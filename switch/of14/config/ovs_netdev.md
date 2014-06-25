---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0036b8a9-1618-45e7-94c0-01377fdd18d3
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 57191335-c610-40a1-9467-2f109a3b3902
controller          : [f14b56e2-1a92-43dd-98a2-12b146b168a4]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1bbe05a9-fa88-4d9b-844f-8aa397521695, 63d1ff17-d9e2-402d-a923-e767b6270562, 74d10574-2b15-4b4b-9ed4-12eeb034de08, ed36edfa-1d80-44ef-8aba-0078594a327a]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f14b56e2-1a92-43dd-98a2-12b146b168a4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=976, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 74d10574-2b15-4b4b-9ed4-12eeb034de08
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [23cc17c5-89ed-41ed-9199-ec2d60bb7745]
name                : br0

_uuid               : 1bbe05a9-fa88-4d9b-844f-8aa397521695
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b32fc001-9e38-4553-98ce-2daaf7c95950]
name                : eth22

_uuid               : ed36edfa-1d80-44ef-8aba-0078594a327a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [97cc0fc8-2cdc-465a-adf9-7db6c2f991fe]
name                : eth21

_uuid               : 63d1ff17-d9e2-402d-a923-e767b6270562
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [55102a2b-c520-4802-93fd-3d8984e25aa9]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 97cc0fc8-2cdc-465a-adf9-7db6c2f991fe
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
statistics          : {collisions=0, rx_bytes=3103992072, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=90963595, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b32fc001-9e38-4553-98ce-2daaf7c95950
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2097607874, tx_dropped=0, tx_errors=0, tx_packets=35808760}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 23cc17c5-89ed-41ed-9199-ec2d60bb7745
admin_state         : down
duplex              : full
ifindex             : 686
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

_uuid               : 55102a2b-c520-4802-93fd-3d8984e25aa9
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=1219397784, tx_dropped=0, tx_errors=0, tx_packets=12266862}
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
