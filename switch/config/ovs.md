---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
bca1ad67-91ae-4e45-84fd-0b7fe0a84ce5
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
_uuid               : d526fb25-1f2d-464e-bcbc-5a8c14063548
controller          : [0f344206-d6c1-4193-aa35-de4668e5c299]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [1c2ff5b0-2989-424d-9b64-1c15e75009d8, 4ceb3747-4a28-4f18-a844-030b3f9ed8c3, c78db1db-34d6-4017-94b5-78055a04179e]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0f344206-d6c1-4193-aa35-de4668e5c299
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=357, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 1c2ff5b0-2989-424d-9b64-1c15e75009d8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9508dc1c-d247-42e0-84ac-7d8c6c53bf9a]
name                : br0

_uuid               : c78db1db-34d6-4017-94b5-78055a04179e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8061b692-cd59-44df-b544-cb5b17d44fd7]
name                : eth8

_uuid               : 4ceb3747-4a28-4f18-a844-030b3f9ed8c3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2d8400ed-fc5d-42ac-9df2-2b83d03c31d4]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9508dc1c-d247-42e0-84ac-7d8c6c53bf9a
admin_state         : up
ifindex             : 120
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

_uuid               : 2d8400ed-fc5d-42ac-9df2-2b83d03c31d4
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

_uuid               : 8061b692-cd59-44df-b544-cb5b17d44fd7
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a66034810666e84377e167ad88ea961caa8b4d17
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Fri Jan 31 15:47:58 2014 -0800
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Fri Jan 31 19:09:45 2014 -0800

    datapth: Suppress error messages on megaflow updates
    
    With subfacets, we'd expect megaflow updates message to carry
    the original micro flow. If not, EINVAL is returned and kernel
    logs an error message.  Now that the user space subfacet layer is
    removed, it is expected that flow updates can arrive with a
    micro flow other than the original. Change the return code to
    EEXIST and remove the kernel error log message.
    
    Reported-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
</pre>
