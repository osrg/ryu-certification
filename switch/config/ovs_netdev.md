---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
da854e96-d900-4026-b90d-31bc2b90629f
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"

$ sudo ovs-vsctl list Bridge
_uuid               : ec847593-64c5-49ac-b2d5-8ed2d627d915
controller          : [214ff765-a39d-4cc7-a790-af9e96ee4afc]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3b9ecda3-34dd-4db5-8f51-92dfb8b0ab98, 47bd6c97-4982-47ba-9eaa-9ce69921a713, a3d2d348-c7c7-4c8d-98dc-032fe9eee046]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 214ff765-a39d-4cc7-a790-af9e96ee4afc
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : a3d2d348-c7c7-4c8d-98dc-032fe9eee046
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6782c541-c30c-4d24-bef9-e45ca40785a6]
name                : "eth7"

_uuid               : 47bd6c97-4982-47ba-9eaa-9ce69921a713
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ed1795f2-ee31-4b9b-a901-cce4f130451e]
name                : "br0"

_uuid               : 3b9ecda3-34dd-4db5-8f51-92dfb8b0ab98
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d1e3d4c2-7ade-4182-8c36-3541acb73f01]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 6782c541-c30c-4d24-bef9-e45ca40785a6
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
statistics          : {collisions=0, rx_bytes=1485416, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=15142, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : ed1795f2-ee31-4b9b-a901-cce4f130451e
admin_state         : up
duplex              : full
ifindex             : 83
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

_uuid               : d1e3d4c2-7ade-4182-8c36-3541acb73f01
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=523564, tx_dropped=0, tx_errors=0, tx_packets=5654}
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
