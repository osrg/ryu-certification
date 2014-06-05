---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
1b6c1fe5-1204-4306-8273-ff699ac54944
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e56f5c0b-bc1e-4417-bc8a-3e856204d7d7
controller          : [54504412-88b4-4e4e-b489-c6a36e54a413]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [2b051550-498d-45ac-a224-f49d11e60c07, 2f3d71a5-2b1e-437e-9957-7329ce63da66, 4c5f8f6f-c62b-4d77-9752-13161078801e, 84a32f6e-56d4-4b27-8668-d972c41f886b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 54504412-88b4-4e4e-b489-c6a36e54a413
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=912, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2b051550-498d-45ac-a224-f49d11e60c07
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [87f3c571-3b8f-4a88-a4c8-b3fa56786d3a]
name                : eth21

_uuid               : 2f3d71a5-2b1e-437e-9957-7329ce63da66
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bf00a8ff-a4bb-4bf4-83c6-847655fce3e2]
name                : eth23

_uuid               : 84a32f6e-56d4-4b27-8668-d972c41f886b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5b7ade69-304a-4a5b-81fb-95b6d4ed83b2]
name                : br0

_uuid               : 4c5f8f6f-c62b-4d77-9752-13161078801e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bbe3fa12-9cd8-41d1-bea1-6815663a2b99]
name                : eth22

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b7ade69-304a-4a5b-81fb-95b6d4ed83b2
admin_state         : down
duplex              : full
ifindex             : 388
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 87f3c571-3b8f-4a88-a4c8-b3fa56786d3a
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=1114799506, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=23707117, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bbe3fa12-9cd8-41d1-bea1-6815663a2b99
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3801071536, tx_dropped=0, tx_errors=0, tx_packets=11144846}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : bf00a8ff-a4bb-4bf4-83c6-847655fce3e2
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=475895908, tx_dropped=0, tx_errors=0, tx_packets=6043887}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6fe0610cf39fe0dc3fc1b11c5cef8afa4eb800c9
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Wed Jun 4 15:47:16 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jun 5 11:36:57 2014 -0700

    poll-loop: Ignore 'wevent' in poll_fd_wait_at&#40;&#41; on non-Windows.
    
    'wevent' isn't actually used on non-Windows systems, but poll_fd_wait_at&#40;&#41;
    and find_poll_node&#40;&#41; treat events with different 'wevent' as different, so
    it seems better to make sure that 'wevent' doesn't matter.
    
    Alternatively, one could ovs_assert&#40;!wevent&#41;.  I guess that would catch
    a caller accidentally swapping the 'fd' and 'wevent' arguments.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
