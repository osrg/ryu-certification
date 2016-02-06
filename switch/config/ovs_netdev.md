---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1395adb7-d347-496b-8da8-211246f9f8b5
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b0472708-29ed-4d93-87a3-b903861e4e05
controller          : [6c331cb3-5281-45f5-bd21-7806c5d16bbd]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5248d6c4-ddec-413d-8ddf-0504f014d609, a7797e55-5137-41bf-beaa-ad349a867a03, b9d8a958-3cd0-4f5f-8346-202351cc1bed, cdcc0b18-3b1b-48f4-a550-30c6023cfab4]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6c331cb3-5281-45f5-bd21-7806c5d16bbd
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="666", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b9d8a958-3cd0-4f5f-8346-202351cc1bed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1b32f6f2-cf5f-4060-9738-9ce203adb347]
name                : "eth23"

_uuid               : 5248d6c4-ddec-413d-8ddf-0504f014d609
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a335997d-892a-4573-9610-92074805c8c9]
name                : "br0"

_uuid               : cdcc0b18-3b1b-48f4-a550-30c6023cfab4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f7a39bbb-948d-4d19-b230-1b7afb7040ff]
name                : "eth22"

_uuid               : a7797e55-5137-41bf-beaa-ad349a867a03
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fb688732-f4df-45b8-8527-b21ae233e4d5]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a335997d-892a-4573-9610-92074805c8c9
admin_state         : down
duplex              : full
ifindex             : 772
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

_uuid               : 1b32f6f2-cf5f-4060-9738-9ce203adb347
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

_uuid               : fb688732-f4df-45b8-8527-b21ae233e4d5
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
statistics          : {collisions=0, rx_bytes=45204385720, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30201764, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : f7a39bbb-948d-4d19-b230-1b7afb7040ff
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30541005514, tx_dropped=0, tx_errors=0, tx_packets=20390585}
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
