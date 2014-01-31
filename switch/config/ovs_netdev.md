---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d1386600-aaea-4cf0-8115-0294a40504bb
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
_uuid               : 709bbebd-3c2d-48c7-84fe-0eebd944a363
controller          : [fdc33b94-9e00-42b4-bd7d-822643cada56]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0e2b272c-635f-43d6-88db-e0963773e940, 370f6482-e68e-47aa-a75d-96b8b82ea0e3, 74295a0b-123b-4af2-a2a2-8e03734b54f9]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fdc33b94-9e00-42b4-bd7d-822643cada56
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0e2b272c-635f-43d6-88db-e0963773e940
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3ec2dbee-58c1-42a7-8fd2-444001d3e41b]
name                : eth8

_uuid               : 370f6482-e68e-47aa-a75d-96b8b82ea0e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9998675b-e6af-4166-b1e8-31d5da1d1db4]
name                : eth7

_uuid               : 74295a0b-123b-4af2-a2a2-8e03734b54f9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4c405220-f60e-4caa-bd56-dadc9c050ced]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4c405220-f60e-4caa-bd56-dadc9c050ced
admin_state         : up
duplex              : full
ifindex             : 105
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

_uuid               : 3ec2dbee-58c1-42a7-8fd2-444001d3e41b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=626402, tx_dropped=0, tx_errors=0, tx_packets=6694}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 9998675b-e6af-4166-b1e8-31d5da1d1db4
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
statistics          : {collisions=0, rx_bytes=3053386293, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72535317, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit b1705c56f366d7dd47c60fed13229db022ce3198
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Mon Jan 27 18:18:33 2014 -0800
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Mon Jan 27 18:25:23 2014 -0800

    datapath: Fix ovs_flow_free() ovs-lock assert.
    
    ovs_flow_free() is not called under ovs-lock during packet
    execute path (ovs_packet_cmd_execute()). Since packet execute
    does not touch flow-&gt;mask, there is no need to take that
    lock either. So move assert in case where flow-&gt;mask is checked.
    
    Found by code inspection.
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Jesse Gross &lt;jesse@nicira.com&gt;
</pre>
