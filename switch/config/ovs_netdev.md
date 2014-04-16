---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b3a2622d-d23a-47c9-9641-9d6a9188ada8
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 80f895c7-c87d-4411-964e-0c180b2e117b
controller          : [764a4182-174a-4d74-92b0-3b5958bcc337]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [572727a7-8264-4da9-9823-97228b8e5422, 6a607bca-a29e-4f72-b023-f83616714bf2, 9fb44c88-050b-4291-8ac7-e2489fc3d310]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 764a4182-174a-4d74-92b0-3b5958bcc337
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=542, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9fb44c88-050b-4291-8ac7-e2489fc3d310
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8718c317-a30c-4f4d-90c0-7f0cee3224c9]
name                : eth7

_uuid               : 6a607bca-a29e-4f72-b023-f83616714bf2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [891bd07c-263f-4716-bf5c-e1ed970d1f92]
name                : br0

_uuid               : 572727a7-8264-4da9-9823-97228b8e5422
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fa779ac4-e881-4e14-8ec7-f93ef5a31368]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 891bd07c-263f-4716-bf5c-e1ed970d1f92
admin_state         : down
duplex              : full
ifindex             : 1000
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : fa779ac4-e881-4e14-8ec7-f93ef5a31368
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7518710, tx_dropped=0, tx_errors=0, tx_packets=80146}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 8718c317-a30c-4f4d-90c0-7f0cee3224c9
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
statistics          : {collisions=0, rx_bytes=3076062944, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72765374, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 40dd413d5b5424eb4cd2e6a8558d33f3b7c607ed
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Tue Apr 15 16:28:15 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Wed Apr 16 13:28:15 2014 -0700

    datapath: Fix a double free bug for the sample action
    
    When sample action returns with an error, the skb has already been
    freed. This patch fix a bug to make sure we don't free it again.
</pre>
