---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3ebca513-15c3-4747-a661-ee15799098f8
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2a0c9d9d-5d92-47eb-bfd4-1c011e4f5362
controller          : [2c11e30a-3ebc-4af6-a7e7-46722a1cdec0]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [071ab49f-38b7-4148-bff2-41fa915b31b5, 0c5df422-f689-47a0-87e9-692bfaa5945d, d64406e7-281b-431e-965c-17c26be36a91, f2708335-6fc9-4921-9828-338f4ed93712]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2c11e30a-3ebc-4af6-a7e7-46722a1cdec0
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f2708335-6fc9-4921-9828-338f4ed93712
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4af75b57-91d6-45b5-8567-d6f09c0a777c]
name                : "eth23"

_uuid               : 0c5df422-f689-47a0-87e9-692bfaa5945d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [79a824ba-b08a-4aef-9476-472d11db8165]
name                : "eth21"

_uuid               : d64406e7-281b-431e-965c-17c26be36a91
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d06d5daa-95b5-4f0f-9b85-1f0c1ad9811f]
name                : "eth22"

_uuid               : 071ab49f-38b7-4148-bff2-41fa915b31b5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [36126f85-9000-43ad-bf35-9d19b893a304]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 36126f85-9000-43ad-bf35-9d19b893a304
admin_state         : down
duplex              : full
ifindex             : 774
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

_uuid               : d06d5daa-95b5-4f0f-9b85-1f0c1ad9811f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30541005772, tx_dropped=0, tx_errors=0, tx_packets=20390588}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 79a824ba-b08a-4aef-9476-472d11db8165
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
statistics          : {collisions=0, rx_bytes=45204385978, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30201767, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4af75b57-91d6-45b5-8567-d6f09c0a777c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8574144000, tx_dropped=0, tx_errors=0, tx_packets=5716096}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit afee281f7f4f4b477e5c12bf18fe00d097ce8e96
Author:     Kevin Traynor &lt;kevin.traynor@intel.com&gt;
AuthorDate: Fri Feb 5 17:07:16 2016 +0000
Commit:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
CommitDate: Fri Feb 5 19:06:00 2016 -0800

    netdev-dpdk: Fix dpdk_watchdog failure to quiesce.
    
    Fix issue whereby vhost_thread is waiting for dpdk_watchdog
    thread to quiesce and at the same time dpdk_watchdog thread
    is waiting for vhost_thread to give up dpdk_mutex.
    
    Reported-by: Patrik Andersson R &lt;patrik.r.andersson@ericsson.com&gt;
    Signed-off-by: Patrik Andersson R &lt;patrik.r.andersson@ericsson.com&gt;
    Signed-off-by: Kevin Traynor &lt;kevin.traynor@intel.com&gt;
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
