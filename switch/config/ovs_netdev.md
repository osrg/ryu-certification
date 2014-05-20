---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
aec47f42-b406-4d6d-a36f-8e962ea1049e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a3397a63-324f-45cb-8d6f-87ed76b4dc0f
controller          : [1ded0dc9-b364-4a44-bea2-2aa6eb601cad]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [412922fe-8015-44f7-9d04-0ef63203e840, 57860807-b2bc-4489-94ff-226aab1fc940, 96a6c640-1935-49a9-9047-ac9f5f4484c2, e4657d12-b14f-4676-8479-e43631d71911]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 1ded0dc9-b364-4a44-bea2-2aa6eb601cad
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=562, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 96a6c640-1935-49a9-9047-ac9f5f4484c2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd66c1a7-99f8-4815-aa5a-8fcff9bf63ff]
name                : eth22

_uuid               : e4657d12-b14f-4676-8479-e43631d71911
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [464c7976-9cfa-425f-be6b-fc8afef1bbe8]
name                : eth23

_uuid               : 412922fe-8015-44f7-9d04-0ef63203e840
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [80aaa238-3027-41fd-999d-1f2e24778552]
name                : br0

_uuid               : 57860807-b2bc-4489-94ff-226aab1fc940
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a2a34af0-921d-4aa2-90cb-c7900bf5cedf]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 80aaa238-3027-41fd-999d-1f2e24778552
admin_state         : down
duplex              : full
ifindex             : 91
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

_uuid               : a2a34af0-921d-4aa2-90cb-c7900bf5cedf
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
statistics          : {collisions=0, rx_bytes=2337366748, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1564681, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 464c7976-9cfa-425f-be6b-fc8afef1bbe8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1671822000, tx_dropped=0, tx_errors=0, tx_packets=1114548}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bd66c1a7-99f8-4815-aa5a-8fcff9bf63ff
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=899101822, tx_dropped=0, tx_errors=0, tx_packets=601830}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ac64794acb85a28059c666ef99250971880027b3
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue May 20 11:37:02 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue May 20 11:37:02 2014 -0700

    dpif: Refactor flow dumping interface to make better sense for batching.
    
    Commit a6ce4b9d251 &#40;ofproto-dpif-upcall: Avoid use-after-free in
    revalidate&#40;&#41; corner case.&#41; showed that it is somewhat tricky to correctly
    use the existing dpif flow dumping interface to obtain batches of flows.
    One has to be careful about calling dpif_flow_dump_next_may_destroy_keys&#40;&#41;
    before going on to the next flow.
    
    A better interface is possible, one that is naturally oriented toward
    retrieving batches when that is a useful optimization.  This commit
    replaces the dpif interface by such a design, and updates both the
    implementations and the callers to adopt it.
    
    This is a fairly large change, but I think that the code in
    ofproto-dpif-upcall is easier to understand after the change.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
