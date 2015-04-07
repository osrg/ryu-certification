---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2d2756f3-a633-48ad-b4e4-08c9e8be4dcc
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 6847f979-6cfb-4885-a488-de5b6656ef3d
controller          : [792dfb42-bec0-4376-86fc-9791e0607076]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2edd30fd-4bf9-4387-b7c8-179053ec81dc, 3d4f98ea-3734-459c-b996-e0176ca079f2, a842d781-a987-4115-af54-68d6a549104d, f6ad1c77-0b38-4d33-936c-6aa4e8c52528]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 792dfb42-bec0-4376-86fc-9791e0607076
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="651", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a842d781-a987-4115-af54-68d6a549104d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0804a9d8-7e2d-4de6-87b3-5bce73e7b0e5]
name                : "eth21"

_uuid               : 2edd30fd-4bf9-4387-b7c8-179053ec81dc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c5a96f30-f968-49cd-a6d3-28d76a669b02]
name                : "br0"

_uuid               : 3d4f98ea-3734-459c-b996-e0176ca079f2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7972f079-9db4-48b3-95fd-dc11098b4a74]
name                : "eth23"

_uuid               : f6ad1c77-0b38-4d33-936c-6aa4e8c52528
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7ab0ff53-2ddf-408a-96ca-bee634819b1f]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c5a96f30-f968-49cd-a6d3-28d76a669b02
admin_state         : down
duplex              : full
ifindex             : 873
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

_uuid               : 0804a9d8-7e2d-4de6-87b3-5bce73e7b0e5
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
statistics          : {collisions=0, rx_bytes=1219081487718, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=813085527, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7972f079-9db4-48b3-95fd-dc11098b4a74
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=39944407500, tx_dropped=0, tx_errors=0, tx_packets=26629605}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7ab0ff53-2ddf-408a-96ca-bee634819b1f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=620123702843, tx_dropped=0, tx_errors=0, tx_packets=413576075}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f293a803d9ece7157ec5d098deb1bf29e5de5915
Author:     Kevin Lo &lt;kevlo@FreeBSD.org&gt;
AuthorDate: Tue Apr 7 16:18:47 2015 +0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Apr 7 05:57:52 2015 -0700

    specify -w to set variables for sysctl&#40;8&#41; on NetBSD
    
    We have to specify -w to set tunable sysctls on NetBSD.
    
    Signed-off-by: Kevin Lo &lt;kevlo at FreeBSD.org&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
