---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
75befd50-4efd-4c72-92d2-27ff2faed82d
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : d96a4758-a4f0-492c-a70b-357d5ad87283
controller          : [4a29e904-7312-412d-9957-7f7dfb24bab0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2ae90271-498c-4ac8-87d4-613e335d79b4, 796890ac-0462-4533-a08e-8c0808791876, e43f1425-9e33-4566-99ed-621c7dd2c1da]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4a29e904-7312-412d-9957-7f7dfb24bab0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=242, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 796890ac-0462-4533-a08e-8c0808791876
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [38174b5b-6e20-4944-a6fc-59e320a6f46f]
name                : eth7

_uuid               : e43f1425-9e33-4566-99ed-621c7dd2c1da
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3dcea9bd-c067-4da9-bdb7-24d55673299f]
name                : eth8

_uuid               : 2ae90271-498c-4ac8-87d4-613e335d79b4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bc66346e-ce4d-444e-a0db-199ab28a23b5]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3dcea9bd-c067-4da9-bdb7-24d55673299f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=98778, tx_dropped=0, tx_errors=0, tx_packets=1050}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : bc66346e-ce4d-444e-a0db-199ab28a23b5
admin_state         : up
duplex              : full
ifindex             : 50
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

_uuid               : 38174b5b-6e20-4944-a6fc-59e320a6f46f
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
statistics          : {collisions=0, rx_bytes=438800, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=4415, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 631486bd29dc6cfe2dc7cf65495d308f4c7fca56
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Wed Dec 18 13:55:25 2013 -0800
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Thu Jan 23 16:08:53 2014 -0800

    netdev-dummy: Add support for active stream
    
    The dummy ports thus far only support passive connections. It can
    listen for multiple incoming connection requests but not make active
    connections. This patch adds support of active stream, so that a
    dummy port can be configured with either passive or active connections.
    
    The net result is that dummy ports can now connect to each other,
    without being patch ports. This feature will be useful in adding test
    cases of future commits.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
