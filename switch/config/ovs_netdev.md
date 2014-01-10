---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3469214f-a668-41ef-9766-6c07e3093fa2
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
_uuid               : 508aaa60-7b43-43a4-aa33-0b9173744f3b
controller          : [402404c8-bea9-4910-8eec-5c2028215f45]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1bc8ff32-29eb-4518-b00c-393b42b71149, 20f99d72-b780-4ca3-9cd0-1082e0bf4069, a68228e4-8102-4878-a4ee-6b901cce382a]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 402404c8-bea9-4910-8eec-5c2028215f45
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a68228e4-8102-4878-a4ee-6b901cce382a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [464aa33f-b54c-4b69-94dc-9f582f29ae5d]
name                : br0

_uuid               : 1bc8ff32-29eb-4518-b00c-393b42b71149
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a1f51635-6939-4b28-ad4b-ab7d1e71c365]
name                : eth8

_uuid               : 20f99d72-b780-4ca3-9cd0-1082e0bf4069
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4abfb10d-9abe-4462-8479-d4a6398ac9b9]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4abfb10d-9abe-4462-8479-d4a6398ac9b9
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
statistics          : {collisions=0, rx_bytes=261060, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2640, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : a1f51635-6939-4b28-ad4b-ab7d1e71c365
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=81688, tx_dropped=0, tx_errors=0, tx_packets=880}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 464aa33f-b54c-4b69-94dc-9f582f29ae5d
admin_state         : up
duplex              : full
ifindex             : 35
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
