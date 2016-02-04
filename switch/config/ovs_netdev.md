---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7c9eb7fd-0004-47a1-b2a9-5927e019c69f
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7f243e5b-1df8-4764-9769-a1f8e004415c
controller          : [50b34de9-57cb-41dc-aadc-c085ca5e891e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [4814cad3-86c0-48f8-b61f-b8e5aaea8d30, 5695cb70-2d3f-4b63-98cc-f071065564b1, c2f1adb1-1cc4-43f3-a993-26685c0b7d02, e1aae732-6034-4b7c-951b-5b0d25d1cbe4]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 50b34de9-57cb-41dc-aadc-c085ca5e891e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5695cb70-2d3f-4b63-98cc-f071065564b1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [628ab8a2-7ae6-4190-96ed-7a0eb9188cd9]
name                : "eth23"

_uuid               : c2f1adb1-1cc4-43f3-a993-26685c0b7d02
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4cc914e2-ac57-4b08-9309-f6f901698885]
name                : "eth22"

_uuid               : e1aae732-6034-4b7c-951b-5b0d25d1cbe4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a77373cf-eb6c-40ad-9aca-fa0b096146b5]
name                : "br0"

_uuid               : 4814cad3-86c0-48f8-b61f-b8e5aaea8d30
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ce9ef7f2-b81f-4fdb-bb25-d90fd05518f4]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ce9ef7f2-b81f-4fdb-bb25-d90fd05518f4
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
statistics          : {collisions=0, rx_bytes=44970359438, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30044431, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 628ab8a2-7ae6-4190-96ed-7a0eb9188cd9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8398786500, tx_dropped=0, tx_errors=0, tx_packets=5599191}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4cc914e2-ac57-4b08-9309-f6f901698885
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30435617748, tx_dropped=0, tx_errors=0, tx_packets=20319685}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a77373cf-eb6c-40ad-9aca-fa0b096146b5
admin_state         : down
duplex              : full
ifindex             : 764
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 25c7da846dfaeb19189134f699710e0f5fdbf10c
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Tue Feb 2 20:55:48 2016 -0800
Commit:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
CommitDate: Wed Feb 3 19:43:24 2016 -0800

    cmap: Explain corner case in CMAP_FOR_EACH comment.
    
    Commit d916785ce98c&#40;&quot;dpif-netdev: Fix improper use of CMAP_FOR_EACH.&quot;&#41;
    fixes a problem that's worth documenting.
    
    Requested-by: Jarno Rajahalme &lt;jarno@ovn.org&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
