---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
73a3abc1-714d-485a-a4cb-2b335fc5fee6
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e2b63eff-97b8-4fc7-b7f2-de6cf1469165
controller          : [f9701ee7-42ec-4caa-af9b-5126fb939259]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [05ad894e-f3c2-4515-b5f1-1d48a1d387e1, 30c86ce1-4924-4414-9354-2d154b323423, ef2f2d84-987a-4eee-bb3a-3f5d32729b3f, ef7a5ab9-f5c4-4c43-bb71-f6c8bb0aac01]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f9701ee7-42ec-4caa-af9b-5126fb939259
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ef2f2d84-987a-4eee-bb3a-3f5d32729b3f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [55f0e92e-beb8-4344-a6e7-5de1783b8e3c]
name                : "br0"

_uuid               : ef7a5ab9-f5c4-4c43-bb71-f6c8bb0aac01
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [25e22b43-aa1a-4cc7-9512-988e7141328a]
name                : "eth23"

_uuid               : 30c86ce1-4924-4414-9354-2d154b323423
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [be4b86fe-3c8e-4197-bd9e-0a9c6c115432]
name                : "eth21"

_uuid               : 05ad894e-f3c2-4515-b5f1-1d48a1d387e1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a1a221f1-e04b-4fb4-875a-26fdd6411d96]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a1a221f1-e04b-4fb4-875a-26fdd6411d96
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 55f0e92e-beb8-4344-a6e7-5de1783b8e3c
admin_state         : down
duplex              : full
ifindex             : 365
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

_uuid               : be4b86fe-3c8e-4197-bd9e-0a9c6c115432
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 25e22b43-aa1a-4cc7-9512-988e7141328a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 45f98d4cf831d795fe2a8f3e6a96b028b5617db6
Author:     Russell Bryant &lt;rbryant@redhat.com&gt;
AuthorDate: Tue Aug 18 11:26:21 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Tue Aug 18 11:26:21 2015 -0700

    ovn: Free default db befor exit.
    
    The static result of default_db&#40;&#41; was malloc'd but not freed before
    exit.  Make the static result global and free it before exit.
    
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
