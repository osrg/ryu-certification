---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
87aa0cba-ade8-4bde-91b2-9967e2bf392b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 035c0813-9713-4c6e-936b-134f9428b83c
controller          : [a0187296-8403-4cbf-8f43-86bef452dd4a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [078e88cc-96ad-440d-a310-8df2114cff8c, 4871fc5c-64d3-413a-b260-9de17ccd377e, 5cdc1b8c-d019-4ff3-afbb-60555b11e025, e8e8efeb-54d7-4940-b683-ef3ec488bedd]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a0187296-8403-4cbf-8f43-86bef452dd4a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="667", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4871fc5c-64d3-413a-b260-9de17ccd377e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c086426f-f3c5-4403-ab0d-48dffa5c4a10]
name                : "eth22"

_uuid               : 078e88cc-96ad-440d-a310-8df2114cff8c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6495d284-c04f-4e36-8b8d-3e9cbb05905e]
name                : "eth21"

_uuid               : 5cdc1b8c-d019-4ff3-afbb-60555b11e025
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bbac56af-8beb-461f-b82b-bc9ebc606879]
name                : "eth23"

_uuid               : e8e8efeb-54d7-4940-b683-ef3ec488bedd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [77d84e0b-b7ec-46bc-bc06-a2adc893a605]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6495d284-c04f-4e36-8b8d-3e9cbb05905e
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
statistics          : {collisions=0, rx_bytes=45672444284, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30516434, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c086426f-f3c5-4403-ab0d-48dffa5c4a10
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30751887546, tx_dropped=0, tx_errors=0, tx_packets=20532456}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : bbac56af-8beb-461f-b82b-bc9ebc606879
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=8924755500, tx_dropped=0, tx_errors=0, tx_packets=5949837}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 77d84e0b-b7ec-46bc-bc06-a2adc893a605
admin_state         : down
duplex              : full
ifindex             : 788
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7b383a56a76e2496f630bcfbc8f9b46f82c62081
Author:     Alin Serdean &lt;aserdean@cloudbasesolutions.com&gt;
AuthorDate: Thu Feb 11 01:38:54 2016 +0000
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Wed Feb 10 20:34:50 2016 -0800

    datapath-windows: Refactor sofware offloads and mss
    
    The purpose of this patch is to refactor the software offloads found in
    the VXLAN and GRE code and also to refactor how the maximmum segment
    size for a given NBL is obtained.
    
    This patch introduces two functions OvsApplySWChecksumOnNB and OVSGetTcpMSS.
    
    OVSGetTcpMSS - will return the mss found in a given NBL.
    
    OvsApplySWChecksumOnNB - will compute and set software offloads for a given
                             NBL.
    
    Signed-off-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Acked-by: Sorin Vinturis &lt;svinturis at cloudbasesolutions.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
