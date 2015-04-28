---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6fcdbf54-7855-44ef-ab6f-6bf1274ebe9e
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f09155b0-a4d6-4f50-9a71-a05d5821a9d9
controller          : [9a544bce-49d7-43a1-9dd8-e71154fe3a4f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3010fc5a-0484-4f14-b9ad-2326f869581a, 3ecc066f-9efd-4856-abcf-f7f79f988184, 5f196809-c4cb-48ad-807e-9f49d2b4cefa, fd594f1e-fef6-4616-aabb-a9b215d32f93]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9a544bce-49d7-43a1-9dd8-e71154fe3a4f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="656", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f196809-c4cb-48ad-807e-9f49d2b4cefa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [94ccc297-e37f-43fb-8d3f-db1e59a577ca]
name                : "eth21"

_uuid               : fd594f1e-fef6-4616-aabb-a9b215d32f93
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a005917f-5cff-4644-b2d1-e5efa9c0cfa1]
name                : "eth23"

_uuid               : 3010fc5a-0484-4f14-b9ad-2326f869581a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d4e27a1c-1be7-41a7-bb0e-9c717096069b]
name                : "br0"

_uuid               : 3ecc066f-9efd-4856-abcf-f7f79f988184
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d8cca6d-5fac-4fde-9f1f-e4ee4afa79dc]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d4e27a1c-1be7-41a7-bb0e-9c717096069b
admin_state         : down
duplex              : full
ifindex             : 951
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

_uuid               : 2d8cca6d-5fac-4fde-9f1f-e4ee4afa79dc
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631625914554, tx_dropped=0, tx_errors=0, tx_packets=421256304}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 94ccc297-e37f-43fb-8d3f-db1e59a577ca
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
statistics          : {collisions=0, rx_bytes=1234882003936, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=823644967, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a005917f-5cff-4644-b2d1-e5efa9c0cfa1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=43387873500, tx_dropped=0, tx_errors=0, tx_packets=28925249}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d3de1af728326646d1a9fe686c6230b79e6d64c1
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Mon Apr 27 14:48:46 2015 +0900
Commit:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
CommitDate: Tue Apr 28 10:03:16 2015 +0900

    datapath: Fix check-export-symbol for non-bash shells
    
    Avoid using a bash construct &#40;=~&#41; in the target.
    
    An alternative would be to make the configure script require
    bash explicitly.  &#40;Currently it doesn't and on NetBSD /bin/ksh
    is likely used.&#41;
    
    The code in question was introduced by
    commit b296b82a87326e68773b970284b8e012def0e3ba .
    &#40;&quot;datapath: Check the export of public functions in linux/compat/linux/.&quot;&#41;
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
