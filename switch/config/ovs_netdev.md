---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4085631d-3649-4110-aac6-be4ff0687407
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 99c57c1b-c224-4104-b8eb-c21309178191
controller          : [a3ade6fd-0553-4247-bb6a-4dbaa609150e]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3476799a-81d0-4cd2-8715-010343188267, 79fab504-41c0-49cf-a20b-7d7c667fb45a, a9b17e78-a5cd-4fb9-bb98-7d43f97e58bd]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a3ade6fd-0553-4247-bb6a-4dbaa609150e
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=372, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 79fab504-41c0-49cf-a20b-7d7c667fb45a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [43d4a2af-dd59-4ca8-98c3-6dd732c728c2]
name                : br0

_uuid               : a9b17e78-a5cd-4fb9-bb98-7d43f97e58bd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c79061ca-10ed-4616-a626-8a0e4c272805]
name                : eth7

_uuid               : 3476799a-81d0-4cd2-8715-010343188267
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f2fe8b42-cd76-4075-bc0b-aa2d5641273e]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : f2fe8b42-cd76-4075-bc0b-aa2d5641273e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2968160, tx_dropped=0, tx_errors=0, tx_packets=31678}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c79061ca-10ed-4616-a626-8a0e4c272805
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
statistics          : {collisions=0, rx_bytes=3060733081, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72609571, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 43d4a2af-dd59-4ca8-98c3-6dd732c728c2
admin_state         : up
duplex              : full
ifindex             : 377
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
commit 691e47554dd03dd6492e00bab5bd6d215f5cbd4f
Author:     Flavio Leitner &lt;fbl@redhat.com&gt;
AuthorDate: Thu Feb 27 09:16:34 2014 -0300
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Feb 27 07:41:54 2014 -0800

    ovs-lib: allow non-root users to check service status
    
    It tries to log the status operation, so although non-root
    users can see the current status, the lack of permission
    to write to the log results in an error message.
    
    This changes to log only if the user has the permission to
    write to the log file.
    
    Signed-off-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
