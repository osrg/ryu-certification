---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ef1726eb-0dfa-4e3e-a290-f2f732bf03ef
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge
_uuid               : 320c86c2-97d2-41ef-b460-5d74ef8c6c09
controller          : [24549227-3b8c-4c35-9307-de4bb5656c08]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [01289dee-7ca2-4148-9a67-e71058c66b35, 578c5cd4-440d-4411-a6a9-e7efa47e451d, af3f37a9-0372-42a2-805e-1f35e464bf08]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 24549227-3b8c-4c35-9307-de4bb5656c08
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="352", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 578c5cd4-440d-4411-a6a9-e7efa47e451d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6d5335d9-d6bd-4d84-8f6c-e6419acec323]
name                : "eth8"

_uuid               : af3f37a9-0372-42a2-805e-1f35e464bf08
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1cddd2ac-057c-40b1-a6f7-a84ea9365dfc]
name                : "br0"

_uuid               : 01289dee-7ca2-4148-9a67-e71058c66b35
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d9a9e375-5135-45b2-b2f2-0667ea1c1f16]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 1cddd2ac-057c-40b1-a6f7-a84ea9365dfc
admin_state         : up
ifindex             : 89
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : d9a9e375-5135-45b2-b2f2-0667ea1c1f16
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 6d5335d9-d6bd-4d84-8f6c-e6419acec323
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c4e976db1343aac88dec4b457bdf5d0277f247e6
Author:     Jesse Gross &lt;jesse@nicira.com&gt;
AuthorDate: Fri Jan 3 15:44:28 2014 -0800
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Fri Jan 3 16:08:37 2014 -0800

    datapath: Check for backported sctp_compute_cksum().
    
    This is backported by RHEL7.
    
    Reported-by: Ashok Byahatti &lt;ashok.byahatti@embrane.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
