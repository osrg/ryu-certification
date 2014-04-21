---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
0e7a3f4e-e03c-4078-835a-4352981d7cd4
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a11e597d-b335-4566-8b7d-4a32f60c2401
controller          : [f15962b6-716c-41eb-9805-e250a2de1c5d]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0b84b0de-ac60-4f68-8112-c161394ef557, 2a66de56-e959-4d8c-bd8a-718ded43c668, 825169fa-d4b8-4839-9a42-d33f209490fa, 938be6df-af7e-48fc-99d5-ca1cd0c62159]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f15962b6-716c-41eb-9805-e250a2de1c5d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=571, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2a66de56-e959-4d8c-bd8a-718ded43c668
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f58ed226-7e77-4892-b946-c86bd5de3843]
name                : eth22

_uuid               : 0b84b0de-ac60-4f68-8112-c161394ef557
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a4ecdf0-b861-45b5-9b0e-310dd67a994b]
name                : br0

_uuid               : 825169fa-d4b8-4839-9a42-d33f209490fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7fe168c2-63de-401c-9897-ba84f0b9bcc9]
name                : eth21

_uuid               : 938be6df-af7e-48fc-99d5-ca1cd0c62159
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [26f40e06-f639-450d-aea5-fc569263970f]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0a4ecdf0-b861-45b5-9b0e-310dd67a994b
admin_state         : down
duplex              : full
ifindex             : 1050
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

_uuid               : 7fe168c2-63de-401c-9897-ba84f0b9bcc9
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=187358645, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=126997, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 26f40e06-f639-450d-aea5-fc569263970f
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=85858500, tx_dropped=0, tx_errors=0, tx_packets=57239}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : f58ed226-7e77-4892-b946-c86bd5de3843
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=124772800, tx_dropped=0, tx_errors=0, tx_packets=83986}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 270a2b8e7692fb0102503d9d590d92db80155ea4
Author:     Rami Rosen &lt;ramirose@gmail.com&gt;
AuthorDate: Sun Apr 20 12:19:44 2014 +0300
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Mon Apr 21 09:28:14 2014 -0700

    datapath: remove unneeded declaration of new_vport&#40;&#41;.
    
    This patch removes the new_vport&#40;&#41; forward declaration in datapath.c
    as it is not needed.
    
    Signed-off-by: Rami Rosen &lt;ramirose@gmail.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
