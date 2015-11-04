---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
af0af7eb-4228-4dba-846a-1ae2e5d26227
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8d453a45-7b5b-4a78-9a9f-1b8f1c71e61f
controller          : [e65e4af6-8c55-490a-8bdb-6e3e38af050f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3e182269-8fb6-4fe3-a900-a0b22a090711, c6735464-d933-4079-8970-29833d258b34, ed214f6f-5dda-476b-86f2-a7d77d1d9a19, f222ce39-f735-4dc3-a9fb-4f686f5c6eca]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e65e4af6-8c55-490a-8bdb-6e3e38af050f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c6735464-d933-4079-8970-29833d258b34
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4915a83a-cb30-43cc-be2c-64b8bcf434fe]
name                : "eth21"

_uuid               : f222ce39-f735-4dc3-a9fb-4f686f5c6eca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [111ab231-0100-49d1-a922-968f6a7c1b00]
name                : "eth22"

_uuid               : 3e182269-8fb6-4fe3-a900-a0b22a090711
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [77163cd7-606f-4d4d-8a4e-a1a2402d7eaa]
name                : "eth23"

_uuid               : ed214f6f-5dda-476b-86f2-a7d77d1d9a19
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7a4a1e6b-2703-4223-b520-5a3b50106e9f]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 111ab231-0100-49d1-a922-968f6a7c1b00
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28403012602, tx_dropped=0, tx_errors=0, tx_packets=18952667}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4915a83a-cb30-43cc-be2c-64b8bcf434fe
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
statistics          : {collisions=0, rx_bytes=40535386317, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27063068, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 77163cd7-606f-4d4d-8a4e-a1a2402d7eaa
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5111125500, tx_dropped=0, tx_errors=0, tx_packets=3407417}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7a4a1e6b-2703-4223-b520-5a3b50106e9f
admin_state         : down
duplex              : full
ifindex             : 621
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
commit 0df6430eda565058a297f911fefec7e6f6bbe34f
Author:     Russell Bryant &lt;rbryant@redhat.com&gt;
AuthorDate: Wed Oct 21 16:13:43 2015 -0400
Commit:     Russell Bryant &lt;rbryant@redhat.com&gt;
CommitDate: Wed Nov 4 11:03:18 2015 -0500

    ovn-tutorial: Add a section on ACLs.
    
    Add a section that gives a quick introduction to applying ACLs.  It
    discusses how the ACLs are translated into OVN logical flows. It doesn't
    get down to the OpenFlow level because that's not supported in
    ovs-sandbox yet.  Instead, it provides a reference to an OpenStack
    related blog post that talks about how OVN ACLs are used there and gives
    examples of the resulting OpenFlow flows.
    
    In theory, once we have a userspace conntrack implementation available,
    we'll be able to provide better suppot for it in ovs-sandbox.
    
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Acked-by: Kyle Mestery &lt;mestery@mestery.com&gt;
</pre>
