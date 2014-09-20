---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
011bc3f4-4bfb-4e19-a065-ff54e7752282
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
_uuid               : bc756ac8-2391-41a5-b0c4-5d4ec5476882
controller          : [87658893-736e-4c37-b736-8aebbabf0f77]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1f9919e8-ce7c-4fdb-9247-983a6643cc35, 311d7655-e13a-4e2f-8558-8d74896b7ad3, b7013814-22f0-4fdf-a5ca-c6448b7bb5d2, df21123d-b9f4-4136-9d25-6c5734b2b260]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 87658893-736e-4c37-b736-8aebbabf0f77
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=672, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1f9919e8-ce7c-4fdb-9247-983a6643cc35
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b1cc6a9e-bbad-4f88-947d-b35c37cd8db3]
name                : eth21

_uuid               : b7013814-22f0-4fdf-a5ca-c6448b7bb5d2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [605863ae-ccb8-4e68-a0ca-d3b1f231d0ba]
name                : eth22

_uuid               : df21123d-b9f4-4136-9d25-6c5734b2b260
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [affc35f0-eebb-4845-8c08-af58df52eeb6]
name                : br0

_uuid               : 311d7655-e13a-4e2f-8558-8d74896b7ad3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [794154fa-8e14-4806-ab3f-98058172d53e]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : affc35f0-eebb-4845-8c08-af58df52eeb6
admin_state         : down
duplex              : full
ifindex             : 158
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

_uuid               : 794154fa-8e14-4806-ab3f-98058172d53e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2200421204, tx_dropped=0, tx_errors=0, tx_packets=4330259}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 605863ae-ccb8-4e68-a0ca-d3b1f231d0ba
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2076728310, tx_dropped=0, tx_errors=0, tx_packets=47219417}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b1cc6a9e-bbad-4f88-947d-b35c37cd8db3
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
statistics          : {collisions=0, rx_bytes=4107971021, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=74370103, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ac8c20812b88c4aae7a002420f54d1333e27f784
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Fri Sep 19 16:20:01 2014 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Fri Sep 19 16:50:17 2014 -0700

    dpif-netdev: Fix &#40;packet&#41; memory leaks in the slow path.
    
    If a packet didn't match a rule in the fast path classifier its memory was
    never freed. The issue was particularly clear with DPDK devices because it was
    not possible to process more than ~250000 DPDK mbufs in the slow path.
    
    This commit fixes the problem by:
    * calling dpif_packet_delete&#40;&#41; if the upcalls are disabled
    * passing may_steal==true to dp_netdev_execute_actions&#40;&#41; during normal upcall
      processing
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
