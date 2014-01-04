---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7bf1f699-a55e-4170-b2e4-aa2fe2cb3cee
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
_uuid               : 9dff821e-244c-43ff-977d-ea6e63d6c065
controller          : [6f9691ce-406f-4d2e-9e88-014c673d9385]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5f92739b-3ec2-418b-a820-f39b5e4b97a0, 6252aa9e-fa4d-4635-b303-959e8aaacafe, 67dd777d-e34d-42a7-9646-8b14df6a6286]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 6f9691ce-406f-4d2e-9e88-014c673d9385
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="356", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 67dd777d-e34d-42a7-9646-8b14df6a6286
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3db0734a-61ac-444f-a960-41e8111ea44a]
name                : "eth8"

_uuid               : 6252aa9e-fa4d-4635-b303-959e8aaacafe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [812a66b0-d4a8-4a7d-826f-d8009521091b]
name                : "br0"

_uuid               : 5f92739b-3ec2-418b-a820-f39b5e4b97a0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fe9c7616-db38-4d84-8c7a-29e1b92ecdc6]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 812a66b0-d4a8-4a7d-826f-d8009521091b
admin_state         : up
ifindex             : 85
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

_uuid               : fe9c7616-db38-4d84-8c7a-29e1b92ecdc6
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

_uuid               : 3db0734a-61ac-444f-a960-41e8111ea44a
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
