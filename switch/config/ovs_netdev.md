---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
25a5992e-4c16-4852-b2e8-a2a071894fb2
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
_uuid               : 975a424e-83ad-4f72-abf3-3315f15f788f
controller          : [01d208b4-7cb8-480d-a17f-0173c60f03e0]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4440d132-a380-42e8-9aeb-e82b3439e38b, 99ac4101-fbb0-426c-a5d7-51a5beaa43e0, d4071398-4490-47a3-9d7b-0462751d1683]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 01d208b4-7cb8-480d-a17f-0173c60f03e0
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=381, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d4071398-4490-47a3-9d7b-0462751d1683
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3646e927-fa55-4644-96c8-264f1e4a0c41]
name                : eth7

_uuid               : 99ac4101-fbb0-426c-a5d7-51a5beaa43e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [83cad8af-a48b-4297-8a30-60a102575044]
name                : br0

_uuid               : 4440d132-a380-42e8-9aeb-e82b3439e38b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [22438163-c428-427a-b3c2-695e599275f9]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 83cad8af-a48b-4297-8a30-60a102575044
admin_state         : up
duplex              : full
ifindex             : 443
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

_uuid               : 3646e927-fa55-4644-96c8-264f1e4a0c41
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
statistics          : {collisions=0, rx_bytes=3061580248, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72618173, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 22438163-c428-427a-b3c2-695e599275f9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3217254, tx_dropped=0, tx_errors=0, tx_packets=34332}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1680d3d7e3813258f5050bb8cb10a2543c60e549
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Thu Mar 6 12:55:53 2014 -0800
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Mar 6 16:35:04 2014 -0800

    getrusage-windows: getrusage() for Windows.
    
    We use getrusage mainly to get user CPU time and system CPU time.
    Windows has a GetProcessTimes and GetThreadTimes that does the
    same job. So use them.
    
    We also use getrusage to get page faults. Use GetProcessMemoryInfo()
    for that.
    
    We also get number of context switches, block i/o times and use it for
    debug information when we wake up from poll_block late. I haven't found
    functions for that in Windows. We only use it for debug information, so
    it should be okay not implementing it.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Co-authored-by: Linda Sun &lt;lsun@vmware.com&gt;
    Signed-off-by: Linda Sun &lt;lsun@vmware.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
