---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
088c6b81-821f-4884-8107-a5904dfc6f13
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 42b356ee-7e72-438a-be91-3c9c99c27790
controller          : [a23baf79-d90f-468f-a989-7048d428f443]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6bc0d950-e139-40a5-b8c2-a2114ef9ee0e, 7e8f2e02-e12d-4488-ae6e-e527c141ddb2, dcaea71b-7854-4fc0-b257-1bbc8282dbe4, e6e763c6-33a9-41e1-9166-1ea55ff44abb]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a23baf79-d90f-468f-a989-7048d428f443
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=661, sec_since_disconnect=7, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6bc0d950-e139-40a5-b8c2-a2114ef9ee0e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6c5ada4c-ecf6-4f0b-839b-14e6e1a09adf]
name                : eth23

_uuid               : e6e763c6-33a9-41e1-9166-1ea55ff44abb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9a504182-f8c1-4b27-a049-45b73fa20e89]
name                : eth22

_uuid               : 7e8f2e02-e12d-4488-ae6e-e527c141ddb2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b0020afe-ab0c-4732-af43-05ce13342313]
name                : eth21

_uuid               : dcaea71b-7854-4fc0-b257-1bbc8282dbe4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e09a3a2f-a1f2-4eeb-9034-9156164034e7]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6c5ada4c-ecf6-4f0b-839b-14e6e1a09adf
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3168967500, tx_dropped=0, tx_errors=0, tx_packets=2112645}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 9a504182-f8c1-4b27-a049-45b73fa20e89
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1163355600, tx_dropped=0, tx_errors=0, tx_packets=23692347}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : b0020afe-ab0c-4732-af43-05ce13342313
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
statistics          : {collisions=0, rx_bytes=2625969946, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=33269874, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e09a3a2f-a1f2-4eeb-9034-9156164034e7
admin_state         : down
duplex              : full
ifindex             : 88
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
commit 16ee1400bbff0f001c2075f413da4bee9f9190e8
Author:     Ariel Tubaltsev &lt;atubaltsev@vmware.com&gt;
AuthorDate: Tue Sep 2 11:27:55 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Wed Sep 3 07:40:29 2014 -0700

    vtep: additions to BFD configuration and status reporting
    
    This commit adds default values for some BFD configuration keys
    &#40;bfd_config_local:bfd_dst_mac and bfd_params:enable&#41;. It also adds new
    BFD status keys &#40;bfd_enabled and bfd_info&#41;.
    
    Signed-off-by: Ariel Tubaltsev &lt;atubaltsev@vmware.com&gt;
    Signed-off-by: Bruce Davie &lt;bdavie@vmware.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
