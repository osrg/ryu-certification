---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
91dda5b8-1f6c-48ad-a7a7-d364f9067e52
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 3b44cc33-bd09-432e-9c96-bfcb9daf0f51
controller          : [9c2c8571-efea-4dc8-8bc0-6d454ae6e5c5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [221544df-ed28-467f-80c5-5274a7b5293f, 7b26b980-fbe3-4ed7-a42b-64fa07cba98b, 90caf107-81fb-47ae-be57-1c8ddae713ca, fe08d722-763b-4b28-a77b-bd4b03d5e87b]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9c2c8571-efea-4dc8-8bc0-6d454ae6e5c5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="4", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7b26b980-fbe3-4ed7-a42b-64fa07cba98b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [79a2bc29-55b6-4230-9901-e698d58c200a]
name                : "eth22"

_uuid               : fe08d722-763b-4b28-a77b-bd4b03d5e87b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0e90fe90-3e10-44fc-b706-d60b4e542daf]
name                : "eth23"

_uuid               : 90caf107-81fb-47ae-be57-1c8ddae713ca
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [54e1d75d-7662-4012-8d9f-86a3169ddd30]
name                : "br0"

_uuid               : 221544df-ed28-467f-80c5-5274a7b5293f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cb5984ce-8c5e-4022-8927-436efdea6d3f]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0e90fe90-3e10-44fc-b706-d60b4e542daf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7609318500, tx_dropped=0, tx_errors=0, tx_packets=5072879}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 54e1d75d-7662-4012-8d9f-86a3169ddd30
admin_state         : down
duplex              : full
ifindex             : 728
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

_uuid               : 79a2bc29-55b6-4230-9901-e698d58c200a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29961719301, tx_dropped=0, tx_errors=0, tx_packets=20000866}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : cb5984ce-8c5e-4022-8927-436efdea6d3f
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
statistics          : {collisions=0, rx_bytes=43917205919, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29336409, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2ad4971f4d6f8dcbc9223161a07e6dd7403f4c7b
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Sat Jan 23 17:17:19 2016 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Mon Jan 25 08:48:44 2016 -0800

    ovs-rcu: Improve comments on ovsrcu_postpone&#40;&#41;.
    
    Suggested-by: William Tu &lt;u9012063@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
