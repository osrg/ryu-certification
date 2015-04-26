---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
38ce64d0-4a91-4563-af76-637b6de030e4
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 01a8ce75-38eb-47ef-ae34-53a7cdbd633b
controller          : [5e20dd5d-40da-42e4-8862-89bd72274c82]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [52ea0b12-88a0-44cb-94a9-64b1ee0aec7d, 5a08cf8a-9271-42de-8e0e-3878c4dd1995, 921cc9d3-763a-448a-978c-b34ea3d74d73, f1656535-493f-435a-9116-25cf9bf43618]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5e20dd5d-40da-42e4-8862-89bd72274c82
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f1656535-493f-435a-9116-25cf9bf43618
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ba274b55-d1da-48df-9033-88c8cd4ab7fa]
name                : "eth22"

_uuid               : 52ea0b12-88a0-44cb-94a9-64b1ee0aec7d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [523b58fb-7912-474e-9610-556fee4b8c6b]
name                : "eth21"

_uuid               : 5a08cf8a-9271-42de-8e0e-3878c4dd1995
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [22da3705-18dc-46d9-a114-da5913c10917]
name                : "eth23"

_uuid               : 921cc9d3-763a-448a-978c-b34ea3d74d73
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e089cc0d-0561-4695-a63f-be9a7c4d0b10]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ba274b55-d1da-48df-9033-88c8cd4ab7fa
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631415693446, tx_dropped=0, tx_errors=0, tx_packets=421114940}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e089cc0d-0561-4695-a63f-be9a7c4d0b10
admin_state         : down
duplex              : full
ifindex             : 943
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

_uuid               : 22da3705-18dc-46d9-a114-da5913c10917
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=43037052000, tx_dropped=0, tx_errors=0, tx_packets=28691368}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 523b58fb-7912-474e-9610-556fee4b8c6b
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
statistics          : {collisions=0, rx_bytes=1234414416136, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=823330672, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b296b82a87326e68773b970284b8e012def0e3ba
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Sun Apr 19 20:54:50 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Sun Apr 26 10:03:44 2015 -0700

    datapath: Check the export of public functions in linux/compat/linux/.
    
    This commit adds check in datapath/Makefile to make sure that all public
    functions and exported symbols in linux/compat/ are either rpl_ or ovs_
    prefixed, except those defined in compat/build-aux/export-check-whitelist.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
