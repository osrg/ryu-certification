---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
596f0f12-a353-40d8-92a8-ac82bd803ed3
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth7"
            Interface "eth7"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : 46e37131-11d7-433d-ba55-050d6a1b3113
controller          : [0cad78a4-c2eb-47c1-bccc-6597aad9fccd]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [43190e07-bc26-43ae-bf59-c37e41e39732, 6e10149f-b451-47ac-8de3-e8b5546ad99d, c21b0ffa-0bd4-4088-9a1d-9ee179cff607]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 0cad78a4-c2eb-47c1-bccc-6597aad9fccd
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="296", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : c21b0ffa-0bd4-4088-9a1d-9ee179cff607
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2e77d4aa-c8d5-4e88-8be3-233265080b18]
name                : "eth8"

_uuid               : 6e10149f-b451-47ac-8de3-e8b5546ad99d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c33809c7-5b6e-481a-b576-6442cf091248]
name                : "br0"

_uuid               : 43190e07-bc26-43ae-bf59-c37e41e39732
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [53bd156b-f9fa-453e-8019-e0a9eee33e2b]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 2e77d4aa-c8d5-4e88-8be3-233265080b18
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=503256, tx_dropped=0, tx_errors=0, tx_packets=5434}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : c33809c7-5b6e-481a-b576-6442cf091248
admin_state         : up
duplex              : full
ifindex             : 81
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : 53bd156b-f9fa-453e-8019-e0a9eee33e2b
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=1420151, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=14482, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 004a624912175a696dc6dd447f267d01cf07ce1f
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Fri Jan 3 09:31:38 2014 -0800
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri Jan 3 09:50:36 2014 -0800

    FAQ: Add entry on GRE module conflicts.
    
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Justin Pettit &lt;jpettit@nicira.com&gt;
</pre>
