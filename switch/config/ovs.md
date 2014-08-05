---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9e3b070b-bb8e-4aab-b9bb-f8d29194d1fd
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 34026c5b-0974-4846-966a-91f94cfa83da
controller          : [a7be4d4f-e8ed-4bdf-b4a9-bcf1cabfdbe2]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [02f17745-3fc2-454f-86ae-f9d2adc57653, 1b94656d-519d-423a-948d-5b40ad3152b6, 31570344-c85d-40d2-a8e4-a7cde32747a7, adfcb104-3b97-440a-8543-4f27d0592417]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a7be4d4f-e8ed-4bdf-b4a9-bcf1cabfdbe2
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=762, sec_since_disconnect=4, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 31570344-c85d-40d2-a8e4-a7cde32747a7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fb2c83de-d6c6-4df9-9176-044f3d5ae02d]
name                : eth21

_uuid               : adfcb104-3b97-440a-8543-4f27d0592417
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [74ea9e78-5bb2-48ea-b060-2af91af945f4]
name                : eth23

_uuid               : 1b94656d-519d-423a-948d-5b40ad3152b6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f45e3af6-850e-466c-88c8-a6a08cb92e80]
name                : br0

_uuid               : 02f17745-3fc2-454f-86ae-f9d2adc57653
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3355469a-fb18-435d-b350-c4fb7c7a42c9]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 74ea9e78-5bb2-48ea-b060-2af91af945f4
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2200840500, tx_dropped=0, tx_errors=0, tx_packets=1467227}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : fb2c83de-d6c6-4df9-9176-044f3d5ae02d
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
statistics          : {collisions=0, rx_bytes=1489671663, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=84054461, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f45e3af6-850e-466c-88c8-a6a08cb92e80
admin_state         : down
ifindex             : 67
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

_uuid               : 3355469a-fb18-435d-b350-c4fb7c7a42c9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1024897228, tx_dropped=0, tx_errors=0, tx_packets=49370516}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 56394293b807ab811903e3655cdf522f0d7146db
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Sun Jul 27 17:51:48 2014 -0700
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Tue Aug 5 14:13:20 2014 -0700

    classifier: classifier_lookup_miniflow_batch&#40;&#41; indicate failures.
    
    This patch causes classifier_lookup_miniflow_batch&#40;&#41; to return a
    boolean indicating whether any rules could not be successfully looked
    up.  Used in future patches.
    
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
