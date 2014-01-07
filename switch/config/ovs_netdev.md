---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
22c5472a-b882-4104-89e2-49002c95abaa
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth7"
            Interface "eth7"
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : f25658c8-d887-4ea9-b1e7-b039dc80454e
controller          : [36df02bd-e916-4e19-b9fb-e3184ee626d8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [8a81c659-aeb7-4008-8d4d-eef6273c850e, a163d166-4080-4f3c-84a6-0b93387b8b0a, ae43a7be-4fe6-4dbb-bb2e-ee8d84ec5154]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 36df02bd-e916-4e19-b9fb-e3184ee626d8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="296", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 8a81c659-aeb7-4008-8d4d-eef6273c850e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [56c8c6f9-38ff-4459-9c9e-419ad56343d0]
name                : "br0"

_uuid               : a163d166-4080-4f3c-84a6-0b93387b8b0a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd23ed0b-f9b6-48b3-8175-657218cda376]
name                : "eth7"

_uuid               : ae43a7be-4fe6-4dbb-bb2e-ee8d84ec5154
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [744d3d96-4335-45fb-82d7-f81b09551053]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : 56c8c6f9-38ff-4459-9c9e-419ad56343d0
admin_state         : up
duplex              : full
ifindex             : 91
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

_uuid               : 744d3d96-4335-45fb-82d7-f81b09551053
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=605480, tx_dropped=0, tx_errors=0, tx_packets=6534}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : bd23ed0b-f9b6-48b3-8175-657218cda376
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
statistics          : {collisions=0, rx_bytes=1746476, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=17782, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
