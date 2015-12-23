---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7c568d52-5a15-4ddf-8746-9c6e50793a16
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f4b84e81-8993-4efc-ad94-6a6fbe7a55c1
controller          : [861a21ac-5ca0-494b-8a3d-7acd071f669a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5208da0f-869a-434a-8b2f-f75433b57e99, 9587bccf-1cc3-417c-b6df-cb5aaafe45a9, b51f8017-cb15-4efc-8d7f-a25b0d615575, cf49f633-d43d-4706-9cb2-3550f33df537]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 861a21ac-5ca0-494b-8a3d-7acd071f669a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="16", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : cf49f633-d43d-4706-9cb2-3550f33df537
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7b744dc4-5361-4420-b3a2-f740b1977bcc]
name                : "eth23"

_uuid               : 5208da0f-869a-434a-8b2f-f75433b57e99
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [08118002-e101-4d9e-939b-51e2ddc06b15]
name                : "br0"

_uuid               : 9587bccf-1cc3-417c-b6df-cb5aaafe45a9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [04cffefa-2bb2-43d0-bcbb-da56c9faa305]
name                : "eth22"

_uuid               : b51f8017-cb15-4efc-8d7f-a25b0d615575
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7a0704d5-897c-4eec-bc61-5dc28bff0ece]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7b744dc4-5361-4420-b3a2-f740b1977bcc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7170787500, tx_dropped=0, tx_errors=0, tx_packets=4780525}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7a0704d5-897c-4eec-bc61-5dc28bff0ece
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
statistics          : {collisions=0, rx_bytes=43332106980, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28943060, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 08118002-e101-4d9e-939b-51e2ddc06b15
admin_state         : down
duplex              : full
ifindex             : 712
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

_uuid               : 04cffefa-2bb2-43d0-bcbb-da56c9faa305
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29698355402, tx_dropped=0, tx_errors=0, tx_packets=19823692}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7ef28119d5984f5e29e07ba4102fc0b680c2a6c9
Author:     William Tu &lt;u9012063@gmail.com&gt;
AuthorDate: Wed Dec 23 10:58:15 2015 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Wed Dec 23 13:03:58 2015 -0800

    ovsdb-server: Fix memory leak using perf counter without initialization.
    
    perf_counter_accumulate&#40;&#41; is invoked without perf_counters_init&#40;&#41; being
    called first, which leads to a memory leak reported by Valgrind &#40;test
    cases 104, 106, and 107&#41;. A call trace is below:
        xmalloc &#40;util.c:112&#41;
        shash_add_nocopy__ &#40;shash.c:109&#41;
        shash_add_nocopy &#40;shash.c:121&#41;
        shash_add &#40;shash.c:129&#41;
        shash_add_once &#40;shash.c:136&#41;
        shash_add_assert &#40;shash.c:146&#41;
        perf_counter_init &#40;perf-counter.c:86&#41;
        perf_counter_accumulate &#40;perf-counter.c:95&#41;
        ovsdb_txn_commit &#40;transaction.c:850&#41;
        ovsdb_file_open__ &#40;file.c:217&#41;
        open_db &#40;ovsdb-server.c:418&#41;
        main &#40;ovsdb-server.c:263&#41;
    
    Signed-off-by: William Tu &lt;u9012063@gmail.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Co-authored-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
