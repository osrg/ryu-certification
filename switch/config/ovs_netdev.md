---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9ffe9d6c-ef29-41de-b1e1-3a79743a4d58
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 91938310-1f28-499c-a85d-ef1c7a37c410
controller          : [ea57a7e4-7517-4b58-a34f-d26304eda4ea]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [b62103c7-ac18-4344-8f0d-1606ccf2789b, ca43d0d5-ae19-4099-b74b-9ae3c80ad0bd, d9b638fb-9487-44d2-880d-26f76f826bd6]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ea57a7e4-7517-4b58-a34f-d26304eda4ea
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ca43d0d5-ae19-4099-b74b-9ae3c80ad0bd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a442a71d-c5c3-407f-9c03-7758f4852439]
name                : eth8

_uuid               : b62103c7-ac18-4344-8f0d-1606ccf2789b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f260b604-4e84-4319-aae9-6198ab0d6ed3]
name                : eth7

_uuid               : d9b638fb-9487-44d2-880d-26f76f826bd6
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [42a8ead3-bc47-4888-b42e-45d5d678c733]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f260b604-4e84-4319-aae9-6198ab0d6ed3
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
statistics          : {collisions=0, rx_bytes=3054169562, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72543238, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : a442a71d-c5c3-407f-9c03-7758f4852439
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=885014, tx_dropped=0, tx_errors=0, tx_packets=9460}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 42a8ead3-bc47-4888-b42e-45d5d678c733
admin_state         : up
duplex              : full
ifindex             : 130
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7343d171c8320bbd5263e518d5ee24d7678488ff
Author:     Daniele Di Proietto &lt;daniele.di.proietto@gmail.com&gt;
AuthorDate: Fri Jan 24 19:00:06 2014 +0100
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Feb 3 15:43:27 2014 -0800

    dpif-linux: remove useless includes
    
    Signed-off-by: Daniele Di Proietto &lt;daniele.di.proietto@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
