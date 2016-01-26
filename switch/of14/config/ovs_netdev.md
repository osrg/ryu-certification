---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
22077639-7210-4b83-b305-4644bca55140
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f84532f-ad8f-4feb-9896-63d4cfab3b27
controller          : [5acd1f51-40ea-44ee-9367-1f1898b6260e]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0fa8c489-b524-46f9-815d-a82782e35af2, 28c1860d-d5e2-4ca2-91af-609a6a6e3bf9, 51ab253e-a711-4c6f-bd7b-ac40adab4608, 7ae75379-1287-4d26-90e2-d158c0a2c416]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5acd1f51-40ea-44ee-9367-1f1898b6260e
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 28c1860d-d5e2-4ca2-91af-609a6a6e3bf9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [19fdc213-68b9-45a0-8061-891817444f22]
name                : "eth22"

_uuid               : 7ae75379-1287-4d26-90e2-d158c0a2c416
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [369bbe94-ff3c-48ed-bc3f-41012f2ed756]
name                : "br0"

_uuid               : 0fa8c489-b524-46f9-815d-a82782e35af2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ea807836-720f-4293-bbd5-446f1ebdcd14]
name                : "eth23"

_uuid               : 51ab253e-a711-4c6f-bd7b-ac40adab4608
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [afd5ec59-0a4a-412b-85b5-63cd51b8e191]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 369bbe94-ff3c-48ed-bc3f-41012f2ed756
admin_state         : down
duplex              : full
ifindex             : 734
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

_uuid               : afd5ec59-0a4a-412b-85b5-63cd51b8e191
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
statistics          : {collisions=0, rx_bytes=44034227568, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29415084, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ea807836-720f-4293-bbd5-446f1ebdcd14
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7696948500, tx_dropped=0, tx_errors=0, tx_packets=5131299}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 19fdc213-68b9-45a0-8061-891817444f22
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30014465942, tx_dropped=0, tx_errors=0, tx_packets=20036354}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 02ab4b1a6a173979a51cabd7000a34546d517e60
Author:     mweglicx &lt;michalx.weglicki@intel.com&gt;
AuthorDate: Wed Dec 23 10:20:22 2015 +0000
Commit:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
CommitDate: Mon Jan 25 18:37:17 2016 -0800

    Update relevant artifacts to add support for DPDK v2.2.0.
    
    Following changes have been applied:
     - INSTALL.DPDK.md: change DPDK version number,
     - build.sh: change DPDK version number.
    
    Signed-off-by: Michal Weglicki &lt;michalx.weglicki@intel.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
