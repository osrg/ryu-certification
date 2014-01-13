---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
15607d6c-5f97-489a-bc97-af5e3f2d488b
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
_uuid               : 1146f86d-dfe5-425e-b969-448d850595ac
controller          : [2e7f00e1-814e-44dc-ae17-ef532a4192e1]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3580211e-32bd-4817-bb88-02ab3ca46d1a, 5cf932bd-6ec9-48ca-a08c-53f9fb6ee1b5, 9d414749-d610-4827-8034-1e6d74fa95cb]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 2e7f00e1-814e-44dc-ae17-ef532a4192e1
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=352, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9d414749-d610-4827-8034-1e6d74fa95cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [84b67274-7772-44e5-b45d-156382afd8c1]
name                : br0

_uuid               : 5cf932bd-6ec9-48ca-a08c-53f9fb6ee1b5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fb94f497-f257-4e91-bee5-ea2890c12a0a]
name                : eth7

_uuid               : 3580211e-32bd-4817-bb88-02ab3ca46d1a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [003f2c6e-3f77-4bee-a30c-4f0727742d7e]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 84b67274-7772-44e5-b45d-156382afd8c1
admin_state         : up
ifindex             : 59
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

_uuid               : 003f2c6e-3f77-4bee-a30c-4f0727742d7e
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

_uuid               : fb94f497-f257-4e91-bee5-ea2890c12a0a
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
commit db1fc2103d73ae0451f569200e70e808a7d7d79f
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Mon Jan 13 13:50:22 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Jan 13 13:50:45 2014 -0800

    netlink: Update comment for nl_dump_start().
    
    The function comment still referred to a 'msg' variable, which has been
    renamed.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    [blp@nicira.com did further proofreading]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
