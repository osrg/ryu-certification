---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
9d15b0ff-7684-4076-ad32-c8a46205231a
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8a351c33-4c48-4009-828b-a39ca2c82e89
controller          : [554d0eae-90ca-44f7-9525-d5b124ddb66c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [27d55fed-4596-4448-877c-b08102b4f30f, ae576dfc-9cb2-464e-af47-c07c4f9067e2, ec567935-bf6a-4760-b4bb-adffb6d444df]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 554d0eae-90ca-44f7-9525-d5b124ddb66c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ae576dfc-9cb2-464e-af47-c07c4f9067e2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ddc89253-a07e-4511-a399-e6af43f049cc]
name                : eth7

_uuid               : 27d55fed-4596-4448-877c-b08102b4f30f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8a57a2f7-6915-4808-9b2f-a8b7523c723e]
name                : eth8

_uuid               : ec567935-bf6a-4760-b4bb-adffb6d444df
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2a1b069a-7f24-4cc8-885f-87753267fefd]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2a1b069a-7f24-4cc8-885f-87753267fefd
admin_state         : up
duplex              : full
ifindex             : 169
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

_uuid               : 8a57a2f7-6915-4808-9b2f-a8b7523c723e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1224532, tx_dropped=0, tx_errors=0, tx_packets=13086}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : ddc89253-a07e-4511-a399-e6af43f049cc
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
statistics          : {collisions=0, rx_bytes=3055191772, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72553559, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e731d71bf47b8370e4bfa87827113eedd20b7398
Author:     Arun Sharma &lt;arun.sharma@calsoftinc.com&gt;
AuthorDate: Thu Feb 6 16:04:05 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Feb 6 16:08:34 2014 -0800

    Add IPv6 support for OpenFlow, OVSDB, NetFlow, and sFlow.
    
    Does not add IPv6 support for in-band control.
    
    Co-authored-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Nandan Nivgune &lt;nandan.nivgune@calsoftinc.com&gt;
    Signed-off-by: Abhijit Bhopatkar &lt;abhijit.bhopatkar@calsoftinc.com&gt;
    Signed-off-by: Arun Sharma &lt;arun.sharma@calsoftinc.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
