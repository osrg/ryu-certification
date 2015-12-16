---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1072b034-081f-407d-9bf0-4695bf06d2c4
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 348c2260-a480-42b6-b8ab-c443aaa51ea5
controller          : [e9886f91-eece-4595-a0db-24a161c58f26]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [151b7d55-9925-408c-9f47-f35daf37c96e, 2b510184-2630-4fec-beea-e6ec6a3e7d5f, 2daf2cc8-5879-4e4b-a52c-71aafc167464, a966e6ad-ce61-462b-b78a-86677d6d7a93]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e9886f91-eece-4595-a0db-24a161c58f26
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2b510184-2630-4fec-beea-e6ec6a3e7d5f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b3aa1a80-7d1d-4432-b9e4-2f14326a2849]
name                : "eth23"

_uuid               : 2daf2cc8-5879-4e4b-a52c-71aafc167464
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d42bf51-f77b-41f4-80ca-ea1fe16d3417]
name                : "eth21"

_uuid               : 151b7d55-9925-408c-9f47-f35daf37c96e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e13cce11-b1d2-4e63-8379-85d3bef54986]
name                : "eth22"

_uuid               : a966e6ad-ce61-462b-b78a-86677d6d7a93
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [706707d4-888c-4b8b-980d-6bfc534b97ea]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b3aa1a80-7d1d-4432-b9e4-2f14326a2849
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6644245500, tx_dropped=0, tx_errors=0, tx_packets=4429497}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 706707d4-888c-4b8b-980d-6bfc534b97ea
admin_state         : down
duplex              : full
ifindex             : 690
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

_uuid               : 3d42bf51-f77b-41f4-80ca-ea1fe16d3417
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
statistics          : {collisions=0, rx_bytes=42629969892, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28471025, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : e13cce11-b1d2-4e63-8379-85d3bef54986
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29382603362, tx_dropped=0, tx_errors=0, tx_packets=19611269}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e7b438dc3014c42aa5a0b4436ec4a67790f06d39
Author:     Gurucharan Shetty &lt;guru@ovn.org&gt;
AuthorDate: Tue Dec 15 08:27:15 2015 -0800
Commit:     Gurucharan Shetty &lt;guru@ovn.org&gt;
CommitDate: Wed Dec 16 10:26:24 2015 -0800

    ovn-ctl: Add daemon status functions.
    
    Signed-off-by: Gurucharan Shetty &lt;guru@ovn.org&gt;
    Acked-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
