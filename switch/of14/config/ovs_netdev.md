---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
281c69cc-4dbb-4a8f-bab9-ee0b3ffaf775
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
_uuid               : c201784e-8372-4c21-a976-de235fa36084
controller          : [53eb1aa7-cff9-4c84-ac76-2acd15f61c3f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [229b3b83-72f1-406e-af80-5be2ab577bab, a2bcc1c7-dc0c-41bf-8998-aa874f84e5fb, b6200759-f4b2-4ffd-94e4-ec4f0cfa4512, cecb5163-2172-4dad-852f-760b8b6d80e6]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 53eb1aa7-cff9-4c84-ac76-2acd15f61c3f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="651", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b6200759-f4b2-4ffd-94e4-ec4f0cfa4512
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c5e79a8b-876f-4c75-b947-542a72e36c74]
name                : "eth22"

_uuid               : 229b3b83-72f1-406e-af80-5be2ab577bab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [82be87cf-8e48-44d3-8636-fc70d0a14ca4]
name                : "eth21"

_uuid               : a2bcc1c7-dc0c-41bf-8998-aa874f84e5fb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [82ae60cb-dd4b-4ba9-a049-8bbed9c8fd9c]
name                : "eth23"

_uuid               : cecb5163-2172-4dad-852f-760b8b6d80e6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [212ad0d0-7cb7-4c99-a283-f0bcd63a6204]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 212ad0d0-7cb7-4c99-a283-f0bcd63a6204
admin_state         : down
duplex              : full
ifindex             : 945
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

_uuid               : 82ae60cb-dd4b-4ba9-a049-8bbed9c8fd9c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=43124491500, tx_dropped=0, tx_errors=0, tx_packets=28749661}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 82be87cf-8e48-44d3-8636-fc70d0a14ca4
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
statistics          : {collisions=0, rx_bytes=1234531319461, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=823409250, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c5e79a8b-876f-4c75-b947-542a72e36c74
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631468520223, tx_dropped=0, tx_errors=0, tx_packets=421150462}
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
