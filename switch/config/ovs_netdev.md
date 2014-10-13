---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3affeeca-a562-4e11-a665-e4c83aa9431b
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : cc7309bd-a578-4ac7-a917-4308db8ddb18
controller          : [b45789bd-95ce-4933-9ebe-4858e4cd61fa]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0d5b1cec-eac6-4626-b833-4becb0695f35, 37244809-d142-4ba5-8dca-814aaafabb16, 765b0c85-f617-46a9-b7a8-0f53706687ab, b0a4913a-c3f9-49d5-9858-a596ec338b17]
protocols           : [OpenFlow13]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b45789bd-95ce-4933-9ebe-4858e4cd61fa
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=697, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0d5b1cec-eac6-4626-b833-4becb0695f35
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5fb90c7d-2906-48af-82b2-ee2880e39d4c]
name                : eth21

_uuid               : 37244809-d142-4ba5-8dca-814aaafabb16
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [031fbd80-bf6b-4ebe-81b4-07fed1a4565d]
name                : eth23

_uuid               : 765b0c85-f617-46a9-b7a8-0f53706687ab
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a699d0b2-6931-409d-b2f2-11586902c3b3]
name                : eth22

_uuid               : b0a4913a-c3f9-49d5-9858-a596ec338b17
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1da75a17-d1d8-4d82-af66-cfae7e6e6a71]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 031fbd80-bf6b-4ebe-81b4-07fed1a4565d
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1957042408, tx_dropped=0, tx_errors=0, tx_packets=7031318}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5fb90c7d-2906-48af-82b2-ee2880e39d4c
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=1777500449, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=161612706, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a699d0b2-6931-409d-b2f2-11586902c3b3
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2334185274, tx_dropped=0, tx_errors=0, tx_packets=98945629}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 1da75a17-d1d8-4d82-af66-cfae7e6e6a71
admin_state         : down
duplex              : full
ifindex             : 240
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 06021dcba984a0e229140179d25d060659bb60a8
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Fri Oct 10 08:21:18 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Mon Oct 13 11:03:11 2014 -0700

    datapath: compat: Fix compilation 3.11
    
    Kernel 3.11 is only kernel where GRE APIs are available but
    not vxlan. Add check for vxlan xmit to detect this case.
    
    Reported-by: Dave Benson &lt;dbenson@verdantnetworks.com&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
