---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d436bd0e-da7b-4d56-9445-bed2d1353ef8
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
_uuid               : 5d1a69eb-b84e-4759-9086-d183677ef33b
controller          : [aafd9218-872e-47ad-a193-b9a35cd7c9ce]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [131a4333-2631-4a2d-8341-7c5d0f2282e5, 1a902f72-0d84-46cd-bd87-2f364005eb99, 88437865-d3ac-4667-abb2-02efe95c37e0, f63af6dc-dc5f-444c-873e-20da16147689]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : aafd9218-872e-47ad-a193-b9a35cd7c9ce
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="672", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f63af6dc-dc5f-444c-873e-20da16147689
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d24bff2f-fec9-436a-a85d-bba6f6e47db8]
name                : "eth23"

_uuid               : 88437865-d3ac-4667-abb2-02efe95c37e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [435986a7-43b3-4bab-8e63-fd40dd08bd3e]
name                : "eth21"

_uuid               : 1a902f72-0d84-46cd-bd87-2f364005eb99
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [43a23734-a0af-47df-94ed-fba75e7bff48]
name                : "eth22"

_uuid               : 131a4333-2631-4a2d-8341-7c5d0f2282e5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [98d7b084-2ddd-4a95-8ed0-8082b17d412a]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 98d7b084-2ddd-4a95-8ed0-8082b17d412a
admin_state         : down
duplex              : full
ifindex             : 852
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

_uuid               : 43a23734-a0af-47df-94ed-fba75e7bff48
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31594766174, tx_dropped=0, tx_errors=0, tx_packets=21099507}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d24bff2f-fec9-436a-a85d-bba6f6e47db8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10327834500, tx_dropped=0, tx_errors=0, tx_packets=6885223}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 435986a7-43b3-4bab-8e63-fd40dd08bd3e
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
statistics          : {collisions=0, rx_bytes=47544680040, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31775115, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3a103e4a99d1d66344277473a5618c34321a59a0
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Thu Mar 3 10:15:14 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Thu Mar 3 12:37:34 2016 -0500

    ovs-ofctl.8: commit is required with alg in ct&#40;&#41;.
    
    The &quot;alg=&quot; argument to the ct&#40;&#41; action only makes sense when used in
    combination with &quot;commit&quot;.  Add this to the documentation to help make
    it clear.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Justin Pettit &lt;jpettit@ovn.org&gt;
</pre>
