---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
660a35dd-4832-4c01-81b8-a4cbac53e2f7
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 97efe66f-08ce-4d93-998d-e4d4b7a822db
controller          : [8ce7fa8d-35e6-4c19-ba41-224d7e3c9100]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2123edfa-d842-4b69-aec0-eb438df261ec, 2a8e6a5d-71ca-4614-ba45-1d914a00a923, 42e8d7cb-f716-4210-944e-b11a54dcd48f, 4a62e891-1706-4046-aaa1-0119e0377eb9]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8ce7fa8d-35e6-4c19-ba41-224d7e3c9100
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=662, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4a62e891-1706-4046-aaa1-0119e0377eb9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [69462361-6c7b-4e30-ae47-2d2ee2259bf3]
name                : eth21

_uuid               : 2a8e6a5d-71ca-4614-ba45-1d914a00a923
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5a6e30c1-adee-45b0-8d4a-ca93df0d67d0]
name                : eth23

_uuid               : 2123edfa-d842-4b69-aec0-eb438df261ec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6a720c8e-e6b1-4878-8a2d-37e6f6a2edd3]
name                : br0

_uuid               : 42e8d7cb-f716-4210-944e-b11a54dcd48f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dcdb73f0-6f9e-4a16-8987-a2ae68dec3d1]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : dcdb73f0-6f9e-4a16-8987-a2ae68dec3d1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2181860630, tx_dropped=0, tx_errors=0, tx_packets=47290091}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 69462361-6c7b-4e30-ae47-2d2ee2259bf3
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
statistics          : {collisions=0, rx_bytes=46772141, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74527211, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 5a6e30c1-adee-45b0-8d4a-ca93df0d67d0
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2375792204, tx_dropped=0, tx_errors=0, tx_packets=4447173}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6a720c8e-e6b1-4878-8a2d-37e6f6a2edd3
admin_state         : down
duplex              : full
ifindex             : 162
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
commit 13a30965fad9df08125bbbce0b2958309f64146e
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Sun Sep 21 11:41:28 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Sun Sep 21 11:52:10 2014 -0700

    datapath: compat: Fix compilation for 2.6.32 kernel
    
    Define alloc_netdev&#40;&#41; using alloc_netdev_mq&#40;&#41; which is available on all
    kernel supported by OVS.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
