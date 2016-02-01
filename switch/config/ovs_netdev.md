---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
18e7da03-d055-493d-9116-3730da06e70b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : eda834be-044c-47ad-ba2d-692b3180cc2d
controller          : [018f0371-4ff7-46ee-953a-839873e5e817]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [57f4c9e3-27a2-4d40-9515-33c174210775, d0123960-a4e2-481c-9ea1-07b36d095740, f64e1884-0f2c-4ec5-ab1d-8c81c13a8dc4, fddd59df-218b-4396-8ab4-f4c56d7e376b]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 018f0371-4ff7-46ee-953a-839873e5e817
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d0123960-a4e2-481c-9ea1-07b36d095740
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [52f2d4a9-5a8d-4d37-89e5-2f061011a2bf]
name                : "eth22"

_uuid               : f64e1884-0f2c-4ec5-ab1d-8c81c13a8dc4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1d5083da-35d6-4c6c-8077-53fec51459f3]
name                : "eth21"

_uuid               : fddd59df-218b-4396-8ab4-f4c56d7e376b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [382f0bfe-b055-4375-aef1-993d398e7fad]
name                : "br0"

_uuid               : 57f4c9e3-27a2-4d40-9515-33c174210775
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [10727aeb-28d6-49b6-968f-443d9cfc19e4]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 52f2d4a9-5a8d-4d37-89e5-2f061011a2bf
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30277704099, tx_dropped=0, tx_errors=0, tx_packets=20213447}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 382f0bfe-b055-4375-aef1-993d398e7fad
admin_state         : down
duplex              : full
ifindex             : 752
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 1d5083da-35d6-4c6c-8077-53fec51459f3
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=44619316265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29808429, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 10727aeb-28d6-49b6-968f-443d9cfc19e4
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8135586000, tx_dropped=0, tx_errors=0, tx_packets=5423724}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d262ac2c60ce1da7b477737f70e8efd38b32502d
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Sun Jan 24 08:32:36 2016 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Mon Feb 1 09:28:02 2016 -0800

    dpif-netdev: Avoid copying netdev_flow_key in emc_processing&#40;&#41;.
    
    Before this commit, emc_processing&#40;&#41; copied a netdev_flow_key if there was
    no exact-match cache &#40;EMC&#41; hit.  This commit eliminates the copy by
    constructing the netdev_flow_key in the place it would be copied.
    
    Found by inspection.
    
    Shahbaz &#40;CCed&#41; reports that this reduces the cost of an EMC miss by 72
    cycles in his test case in which the EMC is disabled.  Presumably this
    is similarly valuable in cases where the EMC merely has few hits.
    
    For the original version of this patch, which was against a slightly
    earlier version of OVS, Daniele reported that:
    
        - With EMC disabled, this increases throughput from 4.8 Mpps to 5.4
          Mpps.
    
        - With EMC enabled, this decreases throughput from 12.4 to 12.0 Mpps.
    
    CC: Muhammad Shahbaz &lt;mshahbaz@cs.princeton.edu&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Andy Zhou &lt;azhou@ovn.org&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
