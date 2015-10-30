---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
11943ec2-171b-4bf5-b207-2aed1d09b37c
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c60adec0-e9f1-41c9-870e-4f21aa0655f6
controller          : [1444f3af-93af-4c8c-b871-040eeb3c0c3b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1ba52d26-32de-445b-b133-b792347cc496, 51041dae-df51-40cc-917a-8186a0944a74, 6a038b10-e398-404b-8aa0-9fe5f8e3d469, edc23409-188e-4256-a883-eb0adfc6c9a3]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1444f3af-93af-4c8c-b871-040eeb3c0c3b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="22", sec_since_disconnect="5", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6a038b10-e398-404b-8aa0-9fe5f8e3d469
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [78ca4325-837f-4e25-b540-12f935e91dd1]
name                : "eth23"

_uuid               : edc23409-188e-4256-a883-eb0adfc6c9a3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e12109dc-75dc-4ce9-94bd-8a144237b6c6]
name                : "eth22"

_uuid               : 1ba52d26-32de-445b-b133-b792347cc496
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b57db77e-8430-4de9-8001-5602c62fd06f]
name                : "br0"

_uuid               : 51041dae-df51-40cc-917a-8186a0944a74
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0f51c082-1864-405e-8b56-63435daccc45]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e12109dc-75dc-4ce9-94bd-8a144237b6c6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28245233794, tx_dropped=0, tx_errors=0, tx_packets=18846646}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 78ca4325-837f-4e25-b540-12f935e91dd1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4847751000, tx_dropped=0, tx_errors=0, tx_packets=3231834}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b57db77e-8430-4de9-8001-5602c62fd06f
admin_state         : down
duplex              : full
ifindex             : 609
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

_uuid               : 0f51c082-1864-405e-8b56-63435daccc45
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
statistics          : {collisions=0, rx_bytes=40184310276, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26827078, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e2167cb7204a94bb1530daa37c4b81661475a583
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Thu Oct 29 14:51:34 2015 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Fri Oct 30 11:13:10 2015 -0700

    test: Make test independent of the recirc_id
    
    Commit 8ae8176fd0d8ed919e3301cc961dcf02b65ff49d &#40;tests: Make test
    independent of the hash function&#41; improves the test &quot;ofprot-dpif
    - balance-tcp bonding, different recirc flow&quot; to not dependent on
    the values of dp-hash, but it still depends on the value of recirc_id,
    which can be a different value based on runs, specifically, it depends
    which one of the two bonds allocates recirc id first.
    
    Since both dp_hash and recirc_id values are runtime dependent,
    consolidate the masking scripts into ofctl_strip.
    
    Bug-report: http://openvswitch.org/pipermail/discuss/2015-October/019269.html
    Reported-by: Gerhrd Stenzel &lt;gstenzel@linux.vnet.ibm.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
