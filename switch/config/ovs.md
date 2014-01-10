---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3f0f118b-1ab6-4faa-a2b7-d0cc477674cb
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge
_uuid               : 28735cfd-adea-4803-ad6c-548962e2e216
controller          : [83a08c98-0aed-4a25-a332-0385c4fada8d]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [85cf1f74-3b20-4eea-9a7a-c3bcfef85a8d, 9993f0e0-0569-4d88-ba69-dd3c5bb3542e, a251c399-a32b-4dd7-af92-a4bd54cf6ca8]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 83a08c98-0aed-4a25-a332-0385c4fada8d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=347, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port
_uuid               : 9993f0e0-0569-4d88-ba69-dd3c5bb3542e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [69e54e00-0cf4-4a36-9e6f-4b1ebe2e897c]
name                : br0

_uuid               : 85cf1f74-3b20-4eea-9a7a-c3bcfef85a8d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [13b66602-08f8-4365-bf7d-fc6a1002ce7b]
name                : eth7

_uuid               : a251c399-a32b-4dd7-af92-a4bd54cf6ca8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [791e42cc-b839-4f3e-9bd7-9ddf57126bd1]
name                : eth8

$ sudo ovs-vsctl list Interface
_uuid               : 69e54e00-0cf4-4a36-9e6f-4b1ebe2e897c
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

_uuid               : 791e42cc-b839-4f3e-9bd7-9ddf57126bd1
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

_uuid               : 13b66602-08f8-4365-bf7d-fc6a1002ce7b
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
