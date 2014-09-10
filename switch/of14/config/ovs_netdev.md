---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2c94d6de-4d08-4b00-9f33-392ab47d7d11
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
_uuid               : 103c382a-aacc-4a3f-aa97-418012357ec1
controller          : [c5b8f1ea-3374-4ac1-a887-590befffab56]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0ecc4159-81de-42e2-94fd-e454fd6b912a, 195a5d27-aae3-4555-a811-e2f093a77886, 74f0b3fb-b4d6-4412-96ac-58b509058047, e7a2002d-b7a2-4928-be39-19d20abfd6c6]
protocols           : [OpenFlow14]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c5b8f1ea-3374-4ac1-a887-590befffab56
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=707, sec_since_disconnect=5, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0ecc4159-81de-42e2-94fd-e454fd6b912a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dc18c34e-8a0d-4f9a-bcd4-086080092008]
name                : br0

_uuid               : e7a2002d-b7a2-4928-be39-19d20abfd6c6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [945a12aa-546f-4ee9-b12b-878d8d968cdd]
name                : eth21

_uuid               : 195a5d27-aae3-4555-a811-e2f093a77886
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b585d0bd-ef1c-4dce-90b5-8b64b3d0596d]
name                : eth23

_uuid               : 74f0b3fb-b4d6-4412-96ac-58b509058047
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8a93468b-c66a-4fa8-9470-0e4864e412b1]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b585d0bd-ef1c-4dce-90b5-8b64b3d0596d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=388506704, tx_dropped=0, tx_errors=0, tx_packets=3122316}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 945a12aa-546f-4ee9-b12b-878d8d968cdd
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
statistics          : {collisions=0, rx_bytes=2114865816, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=64437458, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : dc18c34e-8a0d-4f9a-bcd4-086080092008
admin_state         : down
duplex              : full
ifindex             : 119
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

_uuid               : 8a93468b-c66a-4fa8-9470-0e4864e412b1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3086297186, tx_dropped=0, tx_errors=0, tx_packets=45022842}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2ea824143172e38b4387ef23b8685cebaee21c69
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Tue Sep 24 18:42:43 2013 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Wed Sep 10 13:28:02 2014 -0700

    datapath: Backport __ip_select_ident&#40;&#41; function
    
    definition of __ip_select_ident&#40;&#41; changed in newer kernel and
    it is backported to stable kernel, Therefore adding configure
    check to detect the new function.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
