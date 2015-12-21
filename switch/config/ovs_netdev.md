---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c407bf2b-9908-414a-8eca-b4d4425bbc21
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : dee8db99-7de1-4ed6-b07e-aba6e9a370e4
controller          : [60a3399f-50dc-4ec3-a9c7-92355c03adf5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0d162d2b-4f22-404c-a05a-166622cb8e8d, cac10577-1c37-4c15-b8a6-fcc471001264, d9be0e6f-8b4b-41c6-b965-b1234df9bca9, f283c652-e151-4559-a53d-69db98836ad0]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 60a3399f-50dc-4ec3-a9c7-92355c03adf5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f283c652-e151-4559-a53d-69db98836ad0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [23f5c2e9-e702-402d-84bc-7bc0340fbbca]
name                : "eth22"

_uuid               : d9be0e6f-8b4b-41c6-b965-b1234df9bca9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [be4f9a19-9bb2-472a-84cd-56ad34a5775b]
name                : "eth23"

_uuid               : cac10577-1c37-4c15-b8a6-fcc471001264
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4d6569de-d3cf-44da-b99f-12be6e569909]
name                : "br0"

_uuid               : 0d162d2b-4f22-404c-a05a-166622cb8e8d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1c6b13ff-7089-4d56-8e86-27cb16661be9]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 23f5c2e9-e702-402d-84bc-7bc0340fbbca
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29593141378, tx_dropped=0, tx_errors=0, tx_packets=19752905}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : be4f9a19-9bb2-472a-84cd-56ad34a5775b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6995227500, tx_dropped=0, tx_errors=0, tx_packets=4663485}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 4d6569de-d3cf-44da-b99f-12be6e569909
admin_state         : down
duplex              : full
ifindex             : 702
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

_uuid               : 1c6b13ff-7089-4d56-8e86-27cb16661be9
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
statistics          : {collisions=0, rx_bytes=43098051940, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28785705, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 15a0ca65f341c2298e571052eb68d8a282e853a5
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Sat Dec 19 22:21:56 2015 -0800
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Sun Dec 20 13:20:20 2015 -0800

    datapath: stt: Fix error handling in stt_start&#40;&#41;.
    
    The bug was reported by Joe Stringer.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@kernel.org&gt;
</pre>
