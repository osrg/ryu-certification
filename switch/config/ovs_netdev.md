---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ee560076-3df1-4af6-8db4-fc37afd8e739
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0970fd48-dace-491e-a635-e1caeb5574ea
controller          : [46469b40-3d6d-4905-9a4d-88752884ae04]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [72406e57-d34b-4e9f-92a4-233d85188ea8, 9405353a-8b72-4b3a-bcf3-0244869bbb0d, ca998e5b-95f4-46d9-99fc-58c0ea078f42, f1848f06-c8da-4c38-a8ec-badf2896763d]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 46469b40-3d6d-4905-9a4d-88752884ae04
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9405353a-8b72-4b3a-bcf3-0244869bbb0d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cd12842b-00c0-4427-83d0-a14fca42b9cb]
name                : "eth23"

_uuid               : f1848f06-c8da-4c38-a8ec-badf2896763d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [10e2c05b-36dd-4522-b4e6-90b53f9c2878]
name                : "eth21"

_uuid               : ca998e5b-95f4-46d9-99fc-58c0ea078f42
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f90f3b76-87f4-43c1-969e-262f45db94fd]
name                : "eth22"

_uuid               : 72406e57-d34b-4e9f-92a4-233d85188ea8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [78da7ebb-8e4f-4502-b9a5-cde2754e365a]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f90f3b76-87f4-43c1-969e-262f45db94fd
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31647305557, tx_dropped=0, tx_errors=0, tx_packets=21134854}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : cd12842b-00c0-4427-83d0-a14fca42b9cb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10415680500, tx_dropped=0, tx_errors=0, tx_packets=6943787}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 10e2c05b-36dd-4522-b4e6-90b53f9c2878
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
statistics          : {collisions=0, rx_bytes=47661704431, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31853789, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 78da7ebb-8e4f-4502-b9a5-cde2754e365a
admin_state         : down
duplex              : full
ifindex             : 856
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
commit c26d70a2452ad0d7a13b72c94641d08001283119
Author:     Pravin B Shelar &lt;pshelar@ovn.org&gt;
AuthorDate: Thu Mar 3 16:15:40 2016 -0800
Commit:     Pravin B Shelar &lt;pshelar@ovn.org&gt;
CommitDate: Thu Mar 3 16:15:40 2016 -0800

    datapath: STT: Fix checksum handling.
    
    On packet receive STT verifies the checksum if not done in
    hardware. But IP and TCP were pulled before the verification
    step. The verification expect to see packet with TCP header.
    This causes STT to drop packet in certain cases.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@ovn.org&gt;
    Acked-by: Joe Stringer &lt;joe@ovn.org&gt;
</pre>
