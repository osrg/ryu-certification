---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
efcbada6-5660-4190-897a-e77d12d7c480
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
_uuid               : 7c1ceb6d-1d06-41d9-9cb5-5b7c86a7a17e
controller          : [95342037-6f03-4afa-b12a-d0b1094f28d0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3ac0138d-c68c-4d28-ace1-4758382544a9, 97910195-2426-43d6-a663-e372ed1500bd, a94ba7bb-8a09-42e3-9239-ba1cb6431071]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 95342037-6f03-4afa-b12a-d0b1094f28d0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=296, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3ac0138d-c68c-4d28-ace1-4758382544a9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f78a4c97-fdd7-42f5-b59d-5f3c0237d6e2]
name                : eth7

_uuid               : 97910195-2426-43d6-a663-e372ed1500bd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd97765c-899a-4881-a80f-ce43d87dfc2a]
name                : eth8

_uuid               : a94ba7bb-8a09-42e3-9239-ba1cb6431071
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4cf41c0c-51b2-46e7-ade5-f91363852408]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4cf41c0c-51b2-46e7-ade5-f91363852408
admin_state         : up
duplex              : full
ifindex             : 155
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

_uuid               : bd97765c-899a-4881-a80f-ce43d87dfc2a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1259212, tx_dropped=0, tx_errors=0, tx_packets=13574}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : f78a4c97-fdd7-42f5-b59d-5f3c0237d6e2
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
statistics          : {collisions=0, rx_bytes=3834956, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=38902, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b49c106ef00438b1c59876dad90d00e8d6e7b627
Author:     Flavio Leitner &lt;fbl@redhat.com&gt;
AuthorDate: Thu Jan 9 01:04:33 2014 -0200
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Jan 9 10:57:08 2014 -0800

    fedora package: fix systemd ordering and deps.
    
    There is a chicken and egg issue where common OVS
    configuration uses a controller which is only accessible
    via the network. So starting OVS before network.target
    would break those configurations.
    
    However, the network doesn't come up after boot because
    OVS isn't started until after the network scripts tries
    to configure the ovs.
    
    This is partially fixed by commits:
       commit: 602453000e28ec1076c0482ce13c284765a84409
       rhel: Automatically start openvswitch service before bringing an ovs interfa
    
       commit: 3214851c31538e8690e31f95702f8927a8c0838b
       rhel: Add OVSREQUIRES to automatically bring up OpenFlow interface dependencies
    
    But still there is the dependency issue between network.target
    and openvswitch which this patch fixes it.  It provides two systemd
    service units. One to run at any time (openvswitch-nonetwork.service)
    which runs 'ovs-ctl start' and the other one (openvswith.service) to
    run after network.target which works as a frontend to the admin.
    
    The openvswitch-nonetwork.service is used internally by the
    'ifup-ovs/ifdown-ovs' scripts when adding or removing ports to
    the bridge or when the openvswitch.service is enabled by the admin.
    
    Signed-off-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
