---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b9644f18-4572-4610-bf48-94bc239ab52a
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
_uuid               : dc74b115-bf67-4316-bfbe-c7a19e43d99f
controller          : [0f48705b-a97f-49f9-a183-f7f52ca5c590]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [625f48ab-3af1-4e76-a897-51f116298c3b, b189943e-ea43-4740-9e6e-82508c320226, ede494d0-a881-46af-989d-6711a2d4238a]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 0f48705b-a97f-49f9-a183-f7f52ca5c590
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="356", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : ede494d0-a881-46af-989d-6711a2d4238a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [03122b71-f906-4de9-ac00-6d1378e11886]
name                : "eth8"

_uuid               : b189943e-ea43-4740-9e6e-82508c320226
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e68e5eb5-a9d0-4e9e-9f9b-734383610d77]
name                : "br0"

_uuid               : 625f48ab-3af1-4e76-a897-51f116298c3b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [78e81525-e3be-4768-8d7a-b0d73d1ef25c]
name                : "eth7"

$ sudo ovs-vsctl list Interface
_uuid               : 03122b71-f906-4de9-ac00-6d1378e11886
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

_uuid               : 78e81525-e3be-4768-8d7a-b0d73d1ef25c
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

_uuid               : e68e5eb5-a9d0-4e9e-9f9b-734383610d77
admin_state         : up
ifindex             : 99
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fe68c005871ec5b4b3f33c1b99593667cc83c234
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Tue Jan 7 14:33:37 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jan 7 14:53:25 2014 -0800

    netdev: Update rx_recv documentation for NULL case
    
    Replace truncated description of when rx_recv() may be NULL
    with text used for other fields of netdev_class.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
