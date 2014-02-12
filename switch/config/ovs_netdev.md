---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
231a3573-a255-4f70-ae66-602995934f5f
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1dd61e4f-bdd3-4b60-b2ed-7dabfa5c009e
controller          : [778b7994-2b46-4152-9f96-a5dacab778f1]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4a66247c-07b3-4155-b29c-9b24ea5e149f, 7c9c0d10-2508-4cd7-9f96-c11d710d317c, a72d3741-e5a6-4d5c-a2c7-1e4f8f0135bc]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 778b7994-2b46-4152-9f96-a5dacab778f1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7c9c0d10-2508-4cd7-9f96-c11d710d317c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6c6b09f6-3bd3-4590-be58-6d0938bb9395]
name                : br0

_uuid               : 4a66247c-07b3-4155-b29c-9b24ea5e149f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c770f546-7c9e-4c17-93a9-d458b562b9eb]
name                : eth8

_uuid               : a72d3741-e5a6-4d5c-a2c7-1e4f8f0135bc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [352e44d5-7606-421c-a916-5550fa9e3b3e]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 352e44d5-7606-421c-a916-5550fa9e3b3e
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
statistics          : {collisions=0, rx_bytes=3057329263, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72575103, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 6c6b09f6-3bd3-4590-be58-6d0938bb9395
admin_state         : up
duplex              : full
ifindex             : 248
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

_uuid               : c770f546-7c9e-4c17-93a9-d458b562b9eb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1931468, tx_dropped=0, tx_errors=0, tx_packets=20630}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit dc43709014749ed924d4fcff63055320146cd018
Author:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
AuthorDate: Tue Feb 11 09:49:30 2014 -0800
Commit:     Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
CommitDate: Wed Feb 12 13:58:47 2014 -0800

    ofproto: Move 'rule-&gt;used' to the provider.
    
    Rule's 'used' timestamp is updated at the same time with the other
    stats.  So far the 'used' has been updated without proper protection,
    which may lead to 'tearing' in 32-bit architectures, resulting in an
    incorrect 'used' timestamp.  While in practice this is highly
    improbable, it is still better to handle this correctly.
    
    This is resolved by moving the 'used' field to the provider's stats,
    so that whatever protection is used for updating packet and byte
    counts, can be also used for both reading and writing of the 'used'
    timestamp.
    
    Signed-off-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
