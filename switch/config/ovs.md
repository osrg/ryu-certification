---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
55b7ab51-02fd-49f3-add0-240858799883
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
_uuid               : d249a232-c1e8-4d4f-b059-24d4895ed64e
controller          : [039014a6-0fb8-4f51-83fe-de3851e05d74]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [13829750-bce8-4e83-aab4-298779834c40, 1caaba2a-0faf-4584-8a35-bffc9636034d, f28926e9-e9c7-40c1-b548-cd2cf721ba1d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 039014a6-0fb8-4f51-83fe-de3851e05d74
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=357, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 13829750-bce8-4e83-aab4-298779834c40
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [57bcf1f7-36b2-4ac6-b4de-7ee7d8311bba]
name                : br0

_uuid               : f28926e9-e9c7-40c1-b548-cd2cf721ba1d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d9b3fd2c-c79a-4d1b-9634-73f2a62d5d6c]
name                : eth8

_uuid               : 1caaba2a-0faf-4584-8a35-bffc9636034d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [09513532-55e0-4edc-9edb-bdd8fb14a04e]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d9b3fd2c-c79a-4d1b-9634-73f2a62d5d6c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=20536, tx_dropped=0, tx_errors=0, tx_packets=220}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 09513532-55e0-4edc-9edb-bdd8fb14a04e
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
statistics          : {collisions=0, rx_bytes=65265, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=660, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 57bcf1f7-36b2-4ac6-b4de-7ee7d8311bba
admin_state         : up
ifindex             : 126
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 29dd5cb732fe935246475811cdc9f2a3ac785435
Author:     Daniele Di Proietto &lt;daniele.di.proietto@gmail.com&gt;
AuthorDate: Thu Jan 23 23:26:42 2014 +0100
Commit:     Jesse Gross &lt;jesse@nicira.com&gt;
CommitDate: Mon Feb 3 14:05:30 2014 -0800

    datapath: Added (unsigned long long) cast in printf
    
    This is necessary, since u64 is not unsigned long long
    in all architectures: u64 could be also uint64_t.
    
    Signed-off-by: Daniele Di Proietto &lt;daniele.di.proietto@gmail.com&gt;
    Signed-off-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
