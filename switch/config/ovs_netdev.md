---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
a81625f5-9eb3-4521-a480-ec7a55fb31b7
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
_uuid               : 8d80e1a2-0c95-4527-9013-2284549caa3c
controller          : [ab3dbbc3-744b-456d-9ff9-4ffbb651c434]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5c81c283-61e1-4ea1-8778-9ca81e0fb70a, 69f4e3f2-46bf-4c89-a5a8-a19404ff03bf, 8c52d73f-2196-4e64-a074-88b992ef7bef]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ab3dbbc3-744b-456d-9ff9-4ffbb651c434
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 69f4e3f2-46bf-4c89-a5a8-a19404ff03bf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [49020f7e-5970-4c4e-8563-0ea50a7aeb31]
name                : eth7

_uuid               : 8c52d73f-2196-4e64-a074-88b992ef7bef
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [688b4fc4-f9b4-4dc3-80a9-a8a0b2aea581]
name                : br0

_uuid               : 5c81c283-61e1-4ea1-8778-9ca81e0fb70a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3880a8d0-ec6b-460a-a1fc-f2de9a58d2a2]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3880a8d0-ec6b-460a-a1fc-f2de9a58d2a2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1218368, tx_dropped=0, tx_errors=0, tx_packets=13134}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 688b4fc4-f9b4-4dc3-80a9-a8a0b2aea581
admin_state         : up
duplex              : full
ifindex             : 151
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

_uuid               : 49020f7e-5970-4c4e-8563-0ea50a7aeb31
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
statistics          : {collisions=0, rx_bytes=3704426, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=37582, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
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
