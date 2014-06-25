---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
58fb47c6-382c-4119-8b82-38841366fc5d
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d5bf4b5d-f11d-470d-bc83-f0e189271874
controller          : [7002bba8-a500-44d2-95b5-8e305da93e4e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [00c57e84-669c-4491-8ceb-c72fc2cff871, 9ef2ea56-66b3-4479-baa4-c3a1ced4d207, d8b40c0b-1cef-4413-81ad-3c12134a5751, ffd808c1-2056-4313-a377-30399bf46d86]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7002bba8-a500-44d2-95b5-8e305da93e4e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 00c57e84-669c-4491-8ceb-c72fc2cff871
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3c66f86-940f-46b7-8c69-aa8b464cffdf]
name                : eth23

_uuid               : ffd808c1-2056-4313-a377-30399bf46d86
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ae366e9c-d100-40ad-89f0-88e4439992fe]
name                : br0

_uuid               : 9ef2ea56-66b3-4479-baa4-c3a1ced4d207
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [45f9ada7-b371-4930-b797-1a5387403835]
name                : eth21

_uuid               : d8b40c0b-1cef-4413-81ad-3c12134a5751
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f717e0b5-a3db-4998-9f05-c82914f19b27]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ae366e9c-d100-40ad-89f0-88e4439992fe
admin_state         : down
duplex              : full
ifindex             : 684
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

_uuid               : f717e0b5-a3db-4998-9f05-c82914f19b27
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2056587040, tx_dropped=0, tx_errors=0, tx_packets=35781181}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b3c66f86-940f-46b7-8c69-aa8b464cffdf
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=1120160784, tx_dropped=0, tx_errors=0, tx_packets=12200704}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 45f9ada7-b371-4930-b797-1a5387403835
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
statistics          : {collisions=0, rx_bytes=2987093576, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=90885032, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
