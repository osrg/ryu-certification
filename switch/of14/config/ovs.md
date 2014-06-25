---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d21b3e02-c981-4119-ae05-79814f76adac
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 939935f6-a113-480e-b6f6-2b2f6e0197fe
controller          : [ebae3d79-8623-474b-8b0a-da5db408fde4]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [21633e73-80e8-46b8-83b3-728c8c705434, 2524cc92-820a-4400-8615-22f088f0252f, 780aee25-18ea-49d0-9428-98cdb359740d, 9e86ef29-f6a8-40a5-b2be-db88328e0d30]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ebae3d79-8623-474b-8b0a-da5db408fde4
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9e86ef29-f6a8-40a5-b2be-db88328e0d30
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4aaf07ea-ff60-44e0-ac91-810876005ef1]
name                : br0

_uuid               : 780aee25-18ea-49d0-9428-98cdb359740d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [87872cf9-0d2e-4c60-b7c7-a226fa75e234]
name                : eth21

_uuid               : 2524cc92-820a-4400-8615-22f088f0252f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dca6829a-829f-4b02-af26-68fbc2cd31bf]
name                : eth22

_uuid               : 21633e73-80e8-46b8-83b3-728c8c705434
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e441ea41-43fe-4606-9634-f13b90e9ae69]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 87872cf9-0d2e-4c60-b7c7-a226fa75e234
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
statistics          : {collisions=0, rx_bytes=2870189080, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=90806465, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e441ea41-43fe-4606-9634-f13b90e9ae69
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=1020895284, tx_dropped=0, tx_errors=0, tx_packets=12134527}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : dca6829a-829f-4b02-af26-68fbc2cd31bf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2015591706, tx_dropped=0, tx_errors=0, tx_packets=35753619}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 4aaf07ea-ff60-44e0-ac91-810876005ef1
admin_state         : down
ifindex             : 682
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
