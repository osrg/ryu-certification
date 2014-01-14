---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e7a1506f-59cc-424b-b917-0171195d8869
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
_uuid               : 2f86d39d-85bd-4f18-b434-08640730840c
controller          : [80051099-5f2c-4a28-8982-ebe87a518086]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4055287a-98fa-4a74-920e-e864a5425241, 5ebfd93f-8f19-4ff8-9bf5-79c5e383f665, a6434fb2-71c9-453a-8a75-ac76fe5b5f3d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 80051099-5f2c-4a28-8982-ebe87a518086
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=357, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a6434fb2-71c9-453a-8a75-ac76fe5b5f3d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bec6153e-9e55-42be-a0ae-c088da876173]
name                : eth7

_uuid               : 4055287a-98fa-4a74-920e-e864a5425241
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c9a9c69f-20e2-488d-bfd7-e719e5e9eeca]
name                : eth8

_uuid               : 5ebfd93f-8f19-4ff8-9bf5-79c5e383f665
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [8c4f39d6-cfe3-495b-b80d-d3058ea23e52]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bec6153e-9e55-42be-a0ae-c088da876173
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

_uuid               : 8c4f39d6-cfe3-495b-b80d-d3058ea23e52
admin_state         : up
ifindex             : 65
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

_uuid               : c9a9c69f-20e2-488d-bfd7-e719e5e9eeca
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
commit ed596d3a10ed0eab9aa0c48d5201b1b8046188cc
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Mon Jan 6 08:47:57 2014 -0800
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Jan 14 08:34:48 2014 -0800

    util: Set program_name for windows correctly.
    
    Windows path uses backward slashes. Also, the executable name
    has a .exe extension in it. While creating log files, we use
    the program name to create log file names. It feels a little odd
    to have log file names like ovsdb-server.exe.log etc. Using
    _splitpath_s() is a way to have same log file names on both
    windows and linux platforms.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
