---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cd3ba77d-69f3-4f9b-8374-0cdc6a4d18a2
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
_uuid               : af6013e5-1ed3-4472-b199-4a2a6c1edb0c
controller          : [6f70dfc3-1901-47fc-be35-94a3c01aed3f]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [45d310dd-9ce9-4f9e-97a7-aa71dd2f6688, a9a0f9f5-bf4f-42c1-95d3-979128a6eea4, b98bc8a8-9353-4f13-9ceb-ab36fab29a0c, e5b884db-235e-407e-9267-65cf6ea41d17]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 6f70dfc3-1901-47fc-be35-94a3c01aed3f
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="747", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b98bc8a8-9353-4f13-9ceb-ab36fab29a0c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7bcb8ca4-1d1f-44df-95a1-243cad14d628]
name                : "eth21"

_uuid               : a9a0f9f5-bf4f-42c1-95d3-979128a6eea4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1623167c-c7d4-4f6d-87e3-ee21bfb5cff4]
name                : "eth22"

_uuid               : 45d310dd-9ce9-4f9e-97a7-aa71dd2f6688
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b139c14f-3af8-443f-86b3-ac5335573e6b]
name                : "eth23"

_uuid               : e5b884db-235e-407e-9267-65cf6ea41d17
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [456da4b8-d9fa-4794-92d5-ebd71fc9fcf8]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 456da4b8-d9fa-4794-92d5-ebd71fc9fcf8
admin_state         : down
duplex              : full
ifindex             : 551
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

_uuid               : 7bcb8ca4-1d1f-44df-95a1-243cad14d628
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
statistics          : {collisions=0, rx_bytes=36907804054, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=24624719, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 1623167c-c7d4-4f6d-87e3-ee21bfb5cff4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=26770705540, tx_dropped=0, tx_errors=0, tx_packets=17855910}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b139c14f-3af8-443f-86b3-ac5335573e6b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2391730500, tx_dropped=0, tx_errors=0, tx_packets=1594487}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f0dc83b762bd2645aef975ab01e33b8d69c68840
Author:     Ansis Atteka &lt;aatteka@nicira.com&gt;
AuthorDate: Fri Oct 2 16:46:40 2015 -0700
Commit:     Ansis Atteka &lt;aatteka@nicira.com&gt;
CommitDate: Thu Oct 8 17:32:25 2015 -0700

    RHEL: create /etc/openvswitch directory
    
    This directory needs to be created by the package manager
    because ovs-ctl is being invoked from SElinux openvswitch
    domain that does not have enough privileges to create
    directories under /etc on its own.
    
    Without this patch Open vSwitch is not able to start under
    SElinux enforcing mode &#40;which is default on CentOS by the way&#41;.
    
    Signed-off-by: Ansis Atteka &lt;aatteka@nicira.com&gt;
    Ackedy-by: Kyle Mestery &lt;mestery@mestery.com&gt;
    Acked-by: Flavio Leitner &lt;fbl@sysclose.org&gt;
</pre>
