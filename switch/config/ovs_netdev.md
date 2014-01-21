---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d426e313-e18d-4425-b087-9153c3c67e21
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
_uuid               : a5939511-bd5f-42e6-88fe-77640a6c744b
controller          : [eebc0803-1635-4a3c-a391-83a67c3e5724]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [70e7f293-5563-4a1f-adc2-c157e33578d7, b8da356f-0378-4f65-add5-f6824ac49a49, c193947d-dbbb-40bf-8d10-af0e5c3e4d0d]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : eebc0803-1635-4a3c-a391-83a67c3e5724
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=301, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c193947d-dbbb-40bf-8d10-af0e5c3e4d0d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2b503fd9-9b97-478c-b73d-a8dd98e8b457]
name                : br0

_uuid               : 70e7f293-5563-4a1f-adc2-c157e33578d7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e69b0480-2047-4457-afb6-41799c64f531]
name                : eth7

_uuid               : b8da356f-0378-4f65-add5-f6824ac49a49
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c195c1c8-a14a-4b4a-b52f-b1301735f529]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e69b0480-2047-4457-afb6-41799c64f531
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
statistics          : {collisions=0, rx_bytes=2336045190, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=1585722, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c195c1c8-a14a-4b4a-b52f-b1301735f529
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=952960, tx_dropped=0, tx_errors=0, tx_packets=10246}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 2b503fd9-9b97-478c-b73d-a8dd98e8b457
admin_state         : up
duplex              : full
ifindex             : 119
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
commit c3b758f6fe8b7ae5e3e0204236f6aba48d714bc1
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Dec 5 16:59:13 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Jan 21 09:55:30 2014 -0800

    vlog: Avoid deadlock in vlog_init__() corner case.
    
    Anything inside vlog_init__() that tried to log a message was going to
    deadlock, since it would hit pthread_once() recursively and wait for the
    previous call to complete.  Unfortunately, there was a VLOG_ERR call inside
    vlog_init__(), only called in the corner case where the system's clock was
    wrong.
    
    This fixes the problem by rearranging code so that the logging isn't
    inside the once-only region.
    
    Found by inspection.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
