---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3c805735-7a68-4ba6-8e65-de60ebde2efc
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth8"
            Interface "eth8"
        Port "eth7"
            Interface "eth7"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge
_uuid               : 8b98d491-fdee-4592-87c8-289c62644f9c
controller          : [e86e1713-cf97-4939-aea5-1b5aa812264a]
datapath_id         : "0000000000000001"
datapath_type       : ""
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [038e9917-12d3-456d-890d-46d388c8f343, 55b29492-c0ac-4ffd-adfa-7c32fad47c4e, d29f751d-8804-4f54-b933-2b6b6c4ff3b3]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : e86e1713-cf97-4939-aea5-1b5aa812264a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="346", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : d29f751d-8804-4f54-b933-2b6b6c4ff3b3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3a049fcd-a5e5-43c3-b7f3-0cca4bcd4781]
name                : "br0"

_uuid               : 55b29492-c0ac-4ffd-adfa-7c32fad47c4e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dd1d5144-f234-4e24-a746-2eaab6e51a4a]
name                : "eth7"

_uuid               : 038e9917-12d3-456d-890d-46d388c8f343
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e61c77ed-4bc5-494e-9ff2-e36dd3e62780]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : dd1d5144-f234-4e24-a746-2eaab6e51a4a
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

_uuid               : 3a049fcd-a5e5-43c3-b7f3-0cca4bcd4781
admin_state         : up
ifindex             : 115
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

_uuid               : e61c77ed-4bc5-494e-9ff2-e36dd3e62780
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
commit 69630ea06ce4697369d257c47101be88b5b08e1d
Author:     Daniele Venturino &lt;daniele.venturino@m3s.it&gt;
AuthorDate: Wed Jan 8 16:03:07 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jan 8 16:03:59 2014 -0800

    utilities: Wrong command syntax in ovs-vsctl manpage.
    
    The command shown in the man page to disable the STP protocol on a bridge
    is:
    
            ovs-vsctl clear Bridge br0 stp_enable
    
    Calling that, the following warning message is returned:
    
            ovs-vsctl: "clear" operation cannot be applied to column stp_enable
            of table Bridge, which is not allowed to be empty
    
    It seems correct to use the command:
    
            ovs-vsctl set Bridge br0 stp_enable=false
    
    Signed-off-by: Daniele Venturino &lt;daniele.venturino@m3s.it&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
