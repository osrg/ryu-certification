---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ed55396f-d5c9-4d1b-8a2d-1fb93696e768
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b75fb5a1-abfa-441d-b8ae-100b43c11074
controller          : [5ff3c266-2e47-4c97-870d-a9251673043b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [2193bfd6-3c25-48d6-ad4b-55a6a5df63d4, bbe85b30-c0b9-41ce-b3d7-ebeff4375575, ca563c68-12ab-422b-9859-e8be49bd46e8, edfa269b-99bc-4484-8e27-9801615cd83d]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5ff3c266-2e47-4c97-870d-a9251673043b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="11", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bbe85b30-c0b9-41ce-b3d7-ebeff4375575
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [717b3b7d-7754-4191-8fde-e8116068d2b7]
name                : "eth23"

_uuid               : ca563c68-12ab-422b-9859-e8be49bd46e8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ccb67ff5-9c94-4c63-ad22-e7d300a7368d]
name                : "br0"

_uuid               : 2193bfd6-3c25-48d6-ad4b-55a6a5df63d4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8851f4f7-1a71-468f-bced-76da0ebc429a]
name                : "eth22"

_uuid               : edfa269b-99bc-4484-8e27-9801615cd83d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4a33e4a0-5646-49e6-9125-ebae4709c1f0]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4a33e4a0-5646-49e6-9125-ebae4709c1f0
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
statistics          : {collisions=0, rx_bytes=46257528739, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=30909779, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 717b3b7d-7754-4191-8fde-e8116068d2b7
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9363442500, tx_dropped=0, tx_errors=0, tx_packets=6242295}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ccb67ff5-9c94-4c63-ad22-e7d300a7368d
admin_state         : down
duplex              : full
ifindex             : 808
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

_uuid               : 8851f4f7-1a71-468f-bced-76da0ebc429a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31015077961, tx_dropped=0, tx_errors=0, tx_packets=20709520}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 250bd94d1e500a89c76cac944e660bd9c07ac364
Author:     Pravin B Shelar &lt;pshelar@ovn.org&gt;
AuthorDate: Thu Feb 11 01:05:16 2016 -0800
Commit:     Pravin B Shelar &lt;pshelar@ovn.org&gt;
CommitDate: Wed Feb 17 18:29:44 2016 -0800

    tunneling: Disable IPv6 tunnel
    
    There are multiple issues in IPv6 userspace tunnel
    implementation. Even the kernel module that ships with
    2.5 does not support IPv6 tunneling. There is not
    enough time to get all fixes in branch-2.5. So it make
    sense to disable the support on 2.5.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@ovn.org&gt;
    Acked-by: Flavio Leitner &lt;fbl@sysclose.org&gt;
    Acked-by: Thadeu Lima de Souza Cascardo &lt;cascardo@redhat.com&gt;
    Acked-by: Jesse Gross &lt;jesse@kernel.org&gt;
</pre>
