---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6464a04b-386e-4230-b7df-1b2f34223e12
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 093b8084-275d-481f-be78-228499e53727
controller          : [c2bc6579-b9ad-4fab-b7a3-83313de9d6ea]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [26c1f6ff-5841-4a84-a278-0fb956677288, 3a6e54ba-5795-4590-b2da-6ac5c615ee3f, 5f262e7c-caa3-45c3-8cf3-97a07562a8cc, c6d19e81-6139-45f0-88f0-6700d7ecf16d]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c2bc6579-b9ad-4fab-b7a3-83313de9d6ea
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f262e7c-caa3-45c3-8cf3-97a07562a8cc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fdc542ea-8c6c-4aed-a3da-857795a88aaf]
name                : "eth23"

_uuid               : c6d19e81-6139-45f0-88f0-6700d7ecf16d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d1472c7f-0e04-4061-85a6-8521e0499248]
name                : "eth21"

_uuid               : 3a6e54ba-5795-4590-b2da-6ac5c615ee3f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e4b8d79a-2106-431e-b6d4-069e9ab1c565]
name                : "br0"

_uuid               : 26c1f6ff-5841-4a84-a278-0fb956677288
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [62c1f37b-d1b7-43ce-8178-cd1c6b56d27f]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fdc542ea-8c6c-4aed-a3da-857795a88aaf
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

_uuid               : e4b8d79a-2106-431e-b6d4-069e9ab1c565
admin_state         : down
duplex              : full
ifindex             : 210
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

_uuid               : d1472c7f-0e04-4061-85a6-8521e0499248
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

_uuid               : 62c1f37b-d1b7-43ce-8178-cd1c6b56d27f
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 421e24220fc9493683f75fafc7e2ced8ba60bf30
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Fri Jun 26 11:51:29 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jul 1 14:13:46 2015 -0700

    datapath-windows: Rename 'vport-&gt;isPresentOnHv' to 'isAbsentOnHv'
    
    Looking at the code, the flag 'vport-&gt;isPresentOnHv' is actually
    indicating if the vport is present on the Hyper-V switch or not, but the
    logic seems to be inverse. 'isPresentOnHv == TRUE' indicates that the
    vport is not present on the Hyper-V switch. Eg. VXLAN port, would have
    isPresentOnHv == TRUE.
    
    In this patch, we rename the variable to reflect its meaning.
    
    vport-&gt;isAbsentOnHv is TRUE iff:
    - vport is bridge internal port
    - vport is tunnel port
    - vport was added from Hyper-V and also from OVS, but got deleted from
    Hyper-V
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Alin Gabriel Serdean &lt;aserdean@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
