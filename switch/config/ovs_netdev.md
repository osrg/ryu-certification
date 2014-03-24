---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f1e172fc-a7ef-453a-9f9a-febd24d7208d
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d563ed16-1393-4d8b-8205-2d3aa7e39eb7
controller          : [a576ee3e-54f5-4cd8-bb32-1aac03f3d7b9]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [14ddad18-0f14-474d-889c-e7b3bc9b675d, 18b7492d-9208-4ff1-aad6-a937a42b12f5, ebcc613e-2841-44ca-960d-26b1538ad5f1]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a576ee3e-54f5-4cd8-bb32-1aac03f3d7b9
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=382, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 14ddad18-0f14-474d-889c-e7b3bc9b675d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f12fbf20-414c-41bc-ae8a-6a7b09f20b8e]
name                : eth8

_uuid               : 18b7492d-9208-4ff1-aad6-a937a42b12f5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [451524b1-18e4-4e13-a3bd-7e501e9169ba]
name                : eth7

_uuid               : ebcc613e-2841-44ca-960d-26b1538ad5f1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [51ce33ad-9c8b-4b0c-99c7-59f433e54ec0]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f12fbf20-414c-41bc-ae8a-6a7b09f20b8e
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5161272, tx_dropped=0, tx_errors=0, tx_packets=55030}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 51ce33ad-9c8b-4b0c-99c7-59f433e54ec0
admin_state         : up
duplex              : full
ifindex             : 695
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 451524b1-18e4-4e13-a3bd-7e501e9169ba
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3068184106, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72685183, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit fc3431c6a09e625343dd39b57b86839af90a08fd
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Fri Mar 21 10:36:52 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Mon Mar 24 10:56:31 2014 -0700

    packets: packet metadata from flow function instead of macro.
    
    Commit 03fbdf8d9c80a (lib/flow: Retain ODPP_NONE on flow_extract())
    replaced packet metadata initialization function by a macro.
    Visual studio does not like nested structure initialization that
    is done in that macro.
    
    This commit replaces the macro by a function.
    
    CC: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
