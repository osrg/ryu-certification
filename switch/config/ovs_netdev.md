---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
87a9461d-2777-473d-90cb-4f96deeb77f1
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e6d21636-a3bf-4b49-8763-02a2bd8e8c31
controller          : [a44ba328-abe8-4ff2-8de7-6cd1fefea68b]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0419eb59-8d4b-4652-aeab-312f08abd0f5, 5f91a808-7758-48ff-bea5-df06e7ee94fb, 7c47b46e-9d86-41ac-ac79-49efb3445010]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a44ba328-abe8-4ff2-8de7-6cd1fefea68b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f91a808-7758-48ff-bea5-df06e7ee94fb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7253765e-382a-4c09-93ca-8b9f582e0f09]
name                : eth7

_uuid               : 0419eb59-8d4b-4652-aeab-312f08abd0f5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fdb98463-3de5-43e6-b731-058e4f128d98]
name                : br0

_uuid               : 7c47b46e-9d86-41ac-ac79-49efb3445010
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [126c3816-b1df-4d6e-9724-042dc60057ae]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 126c3816-b1df-4d6e-9724-042dc60057ae
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1287986, tx_dropped=0, tx_errors=0, tx_packets=13762}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 7253765e-382a-4c09-93ca-8b9f582e0f09
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
statistics          : {collisions=0, rx_bytes=3055380182, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72555459, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : fdb98463-3de5-43e6-b731-058e4f128d98
admin_state         : up
duplex              : full
ifindex             : 178
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
commit c78a9ead62ddd8179cf6fedd9bd92f6ec17885c0
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Feb 6 21:30:42 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Feb 6 21:30:42 2014 -0800

    FAQ: Describe the state of MPLS in Open vSwitch.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Simon Horman &lt;horms@verge.net.au&gt;
</pre>
