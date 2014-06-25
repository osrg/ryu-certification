---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c925cd95-0c2d-4cce-a969-89ab297758cd
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e97b2376-fa10-405c-8538-72201bcc8f6b
controller          : [9af50d33-9ca2-465f-84a8-fa8e1a4aa2fa]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [43351c18-4dc8-4108-b0f6-513c7abaa584, a49875ed-c0d7-4e1c-b672-61099adaaef8, b0d3cfd8-2de5-42b2-b62d-417abd10a0cf, d84031dc-e51f-4a1b-b5e2-7c66a261d4bc]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 9af50d33-9ca2-465f-84a8-fa8e1a4aa2fa
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d84031dc-e51f-4a1b-b5e2-7c66a261d4bc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ad888761-3dc8-41f5-af8a-53c5583f8c12]
name                : br0

_uuid               : 43351c18-4dc8-4108-b0f6-513c7abaa584
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b26dcf4e-0584-4740-9ce1-ba7f83f8a12b]
name                : eth23

_uuid               : b0d3cfd8-2de5-42b2-b62d-417abd10a0cf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7ef7bb98-bfda-41ef-ab1d-e7bcef0a1626]
name                : eth21

_uuid               : a49875ed-c0d7-4e1c-b672-61099adaaef8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f65f14e6-4687-4832-9ec3-7063520b8c92]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7ef7bb98-bfda-41ef-ab1d-e7bcef0a1626
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
statistics          : {collisions=0, rx_bytes=328745724, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=91984941, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ad888761-3dc8-41f5-af8a-53c5583f8c12
admin_state         : down
ifindex             : 712
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal

_uuid               : b26dcf4e-0584-4740-9ce1-ba7f83f8a12b
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2511269784, tx_dropped=0, tx_errors=0, tx_packets=13128110}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f65f14e6-4687-4832-9ec3-7063520b8c92
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2629107216, tx_dropped=0, tx_errors=0, tx_packets=36166106}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8bb113da32dd2aabcb958bb16941ba73ae4610b3
Author:     Ryan Wilson &lt;wryan@nicira.com&gt;
AuthorDate: Mon Jun 23 12:36:11 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jun 25 12:54:26 2014 -0700

    dpif-netdev: Implement batched flow dumping.
    
    Previously, flows were retrieved one by one when dumping flows for
    datapaths of type 'netdev'. This increased contention for the dump's
    mutex, negatively affecting revalidator performance.
    
    This patch retrieves batches of flows when dumping flows for datapaths
    of type 'netdev'.
    
    Signed-off-by: Ryan Wilson &lt;wryan@nicira.com&gt;
    [blp@nicira.com relaxed max_flows restriction]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
