---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c4dd75ed-a34f-4865-a502-a6d6d0bab89c
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
_uuid               : 5e00fc46-03d6-4d25-bf13-98c1bdf4eb4f
controller          : [785326c4-cd55-4ece-9d5a-a075e13b4ce8]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [21858f87-ee14-4cb5-8a4c-c98fbcc02ce8, b328eb73-5b13-4092-a805-0ea915ab7b7e, e4abc94f-392f-4431-b6d9-d357a504a702]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 785326c4-cd55-4ece-9d5a-a075e13b4ce8
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=366, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 21858f87-ee14-4cb5-8a4c-c98fbcc02ce8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [16e82d5c-8fe1-40a3-b216-a77ec2c57de9]
name                : br0

_uuid               : b328eb73-5b13-4092-a805-0ea915ab7b7e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cbdaee43-eab4-4b2e-8791-0dfe891df7af]
name                : eth7

_uuid               : e4abc94f-392f-4431-b6d9-d357a504a702
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a9485b3e-7995-4f06-b709-146f46b995b5]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 16e82d5c-8fe1-40a3-b216-a77ec2c57de9
admin_state         : up
duplex              : full
ifindex             : 567
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

_uuid               : a9485b3e-7995-4f06-b709-146f46b995b5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4301820, tx_dropped=0, tx_errors=0, tx_packets=45878}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : cbdaee43-eab4-4b2e-8791-0dfe891df7af
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
statistics          : {collisions=0, rx_bytes=3065258846, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72655485, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a27ce57b65959a3fb796ebb20958930624b0732e
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Mar 14 11:47:30 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Mon Mar 17 17:07:54 2014 -0700

    datapath: compat: Downstream the reciprocal_div.{c,h}.
    
    The reciprocal division code used in datapath is flawed.  The bug
    has been fixed in the linux kernel repo in commit 809fa972fd(
    reciprocal_divide: update/correction of the algorithm).
    
    This commit downstreams the reciprocal_div.{c,h} from the linux
    kernel repo.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Reviewed-by: Thomas Graf &lt;tgraf@redhat.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
