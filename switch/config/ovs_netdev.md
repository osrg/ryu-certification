---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
efeb2368-4da2-4998-9660-36278e133177
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
_uuid               : 688b2c7a-2f17-4a27-8683-09878fb043d2
controller          : [09e8d585-0eb2-4819-8b07-3e6af3322794]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [493061ef-cca6-4c93-bfc9-8c2adc6d3ed2, 5089b6f7-d969-4332-80c7-a9ea54088e3b, 5ad39eef-68e9-4557-a0ef-9ad004072461]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 09e8d585-0eb2-4819-8b07-3e6af3322794
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=532, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 493061ef-cca6-4c93-bfc9-8c2adc6d3ed2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [138cb3f6-30bb-49b9-985e-cec3d94a27b8]
name                : eth8

_uuid               : 5089b6f7-d969-4332-80c7-a9ea54088e3b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [89423ea2-deeb-43ef-8676-4ed0bfd29d50]
name                : br0

_uuid               : 5ad39eef-68e9-4557-a0ef-9ad004072461
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7e74760e-2eef-47e8-8679-6e9b01537115]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 89423ea2-deeb-43ef-8676-4ed0bfd29d50
admin_state         : down
duplex              : full
ifindex             : 994
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 138cb3f6-30bb-49b9-985e-cec3d94a27b8
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7471811, tx_dropped=0, tx_errors=0, tx_packets=79646}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 7e74760e-2eef-47e8-8679-6e9b01537115
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
statistics          : {collisions=0, rx_bytes=3075938329, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72764029, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit beb1c69a3a661dbc0232aeb9831c14788f84eb24
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Mon Apr 14 23:37:10 2014 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Mon Apr 14 23:47:37 2014 -0700

    datapath: Allow each vport to have an array of 'port_id's.
    
    In order to allow handlers directly read upcalls from datapath,
    we need to support per-handler netlink socket for each vport in
    datapath.  This commit makes this happen.  Also, it is guaranteed
    to be backward compatible with previous branch.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Thomas Graf &lt;tgraf@redhat.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
