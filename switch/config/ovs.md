---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5ca56ee4-4338-494a-94f3-7a9f6ec4acf9
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 5f3e9a59-4e7e-4588-8718-c885eebcd34e
controller          : [ce392031-bba8-484f-9f5b-bfd30ed4307f]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [02c94e85-aa65-435f-8df4-ea0f4b7682ad, b8e27629-4afa-4d40-9f14-5010bc6e0cd8, fef8b153-ea86-49d3-b7e8-bef5133efbf2]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ce392031-bba8-484f-9f5b-bfd30ed4307f
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=351, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 02c94e85-aa65-435f-8df4-ea0f4b7682ad
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [18761b9e-7319-48e9-9e15-d33f7b80d5b0]
name                : br0

_uuid               : b8e27629-4afa-4d40-9f14-5010bc6e0cd8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4fb9ca65-01b1-4802-a37d-33868bc53e2c]
name                : eth8

_uuid               : fef8b153-ea86-49d3-b7e8-bef5133efbf2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a2e90d5c-0313-401a-b4ac-ff50df48c565]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a2e90d5c-0313-401a-b4ac-ff50df48c565
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

_uuid               : 4fb9ca65-01b1-4802-a37d-33868bc53e2c
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

_uuid               : 18761b9e-7319-48e9-9e15-d33f7b80d5b0
admin_state         : up
ifindex             : 149
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
commit 42dd41ef305bac8be801346e9232788d30f895bd
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Fri Jan 17 10:43:03 2014 -0800
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Feb 4 08:30:00 2014 -0800

    daemon-windows: Add users for windows services.
    
    Start with ovs-vswitchd and ovsdb-server.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
