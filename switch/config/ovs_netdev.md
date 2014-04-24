---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
06ffbeeb-ac76-42ff-8852-c879efa0f790
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 3c47f08e-ede4-472a-b30f-7a6c136578e1
controller          : [9089b00c-d9f5-4b43-81c3-72a042ad61ae]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [17da3cfc-e65c-48d0-992e-74239dbc5991, 1cd09bac-37e2-4393-86a5-f33a6dbde8bc, 8d3f73d3-53ee-40a7-8978-0d475d3a4341, ec02a619-b222-4c77-9e62-b17c919a4612]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9089b00c-d9f5-4b43-81c3-72a042ad61ae
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=566, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 17da3cfc-e65c-48d0-992e-74239dbc5991
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [15d1feba-9b6e-42b7-942d-6d2d92320789]
name                : br0

_uuid               : 1cd09bac-37e2-4393-86a5-f33a6dbde8bc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd9be6bc-96cf-4cb1-b76a-a0e83e555f82]
name                : eth21

_uuid               : ec02a619-b222-4c77-9e62-b17c919a4612
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eb67925b-cdba-421f-8934-43b4cd3c9693]
name                : eth22

_uuid               : 8d3f73d3-53ee-40a7-8978-0d475d3a4341
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e08b4174-0fea-4e8d-a1ed-46d425bcbda8]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e08b4174-0fea-4e8d-a1ed-46d425bcbda8
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1395684000, tx_dropped=0, tx_errors=0, tx_packets=930456}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : cd9be6bc-96cf-4cb1-b76a-a0e83e555f82
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=2744138891, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1845424, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 15d1feba-9b6e-42b7-942d-6d2d92320789
admin_state         : down
duplex              : full
ifindex             : 1131
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

_uuid               : eb67925b-cdba-421f-8934-43b4cd3c9693
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1643972774, tx_dropped=0, tx_errors=0, tx_packets=1102476}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7d1700980b5dcf98003fdceb821d7967fad99786
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Thu Apr 10 07:14:08 2014 +0000
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Thu Apr 24 16:31:01 2014 +1200

    ofproto-dpif-upcall: Remove the flow_dumper thread.
    
    Previously, we had a separate flow_dumper thread that fetched flows from
    the datapath to distribute to revalidator threads. This patch takes the
    logic for dumping and pushes it into the revalidator threads, resulting
    in simpler code with similar performance to the current code.
    
    One thread, the &quot;leader&quot;, is responsible for beginning and ending each
    flow dump, maintaining the flow_limit, and checking whether the
    revalidator threads need to exit. All revalidator threads dump,
    revalidate, delete datapath flows and garbage collect ukeys.
    
    Co-authored-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
