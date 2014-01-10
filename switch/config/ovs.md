---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
57e7045e-ebdb-4d19-bc13-57167ca176e4
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
_uuid               : 6b668057-e0f8-4638-be1c-39178311b582
controller          : [5b2431f8-e381-4758-9913-60c3979632ef]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [10d00985-ea04-473e-8405-cf76821ec1f9, 940c8336-df58-411a-ad12-5a23b4f6fb2a, e9de8fd8-e80f-4c33-a66e-55495a67ac52]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b2431f8-e381-4758-9913-60c3979632ef
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e9de8fd8-e80f-4c33-a66e-55495a67ac52
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8711f5c0-4306-4746-91e3-cacb654e4f20]
name                : br0

_uuid               : 10d00985-ea04-473e-8405-cf76821ec1f9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c8e8be73-9d61-431c-bd75-9b41075b7288]
name                : eth7

_uuid               : 940c8336-df58-411a-ad12-5a23b4f6fb2a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c3ac5e69-5e81-4c13-bcc3-c7ebf9f47481]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 8711f5c0-4306-4746-91e3-cacb654e4f20
admin_state         : up
ifindex             : 153
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

_uuid               : c3ac5e69-5e81-4c13-bcc3-c7ebf9f47481
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

_uuid               : c8e8be73-9d61-431c-bd75-9b41075b7288
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
