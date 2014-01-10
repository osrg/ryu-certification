---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2574c86e-797d-43c3-84b2-117890f8443f
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 206a5025-7c8e-4825-adec-4dc34ec495a8
controller          : [a62ebd8a-6820-4ba4-a535-9b5ceb1c0cde]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [35b34d24-7436-4fd2-ae1b-0ece5b5eb865, c4d69b65-9556-44e6-88c9-19d2f7367f2d, cf8b5e4f-c98e-4dce-a70b-1a5d291ee62b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a62ebd8a-6820-4ba4-a535-9b5ceb1c0cde
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 35b34d24-7436-4fd2-ae1b-0ece5b5eb865
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f841c779-eae7-46d1-b0e3-74663d45b38f]
name                : eth7

_uuid               : c4d69b65-9556-44e6-88c9-19d2f7367f2d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [993146b8-4121-4eab-9ad3-2466efbbb6f8]
name                : br0

_uuid               : cf8b5e4f-c98e-4dce-a70b-1a5d291ee62b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eece317c-4178-4cee-8937-361c32642ea9]
name                : eth8

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 993146b8-4121-4eab-9ad3-2466efbbb6f8
admin_state         : up
duplex              : full
ifindex             : 39
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

_uuid               : eece317c-4178-4cee-8937-361c32642ea9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=122532, tx_dropped=0, tx_errors=0, tx_packets=1320}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : f841c779-eae7-46d1-b0e3-74663d45b38f
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
statistics          : {collisions=0, rx_bytes=391590, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=3960, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit deb64473f677e81f6a63db9c35de501c438e1342
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Dec 31 14:23:34 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Fri Jan 10 10:52:51 2014 -0800

    Update build requirements.
    
    Libtool is now required as of commit 38b7a52b61 (openvswitch: Use libtool
    and allow building shared libs).
    
    It seems that a build requirement for Python slipped in a while back, for
    generating ovs-vswitchd.conf.db.5, and no one complained, so we might as
    well make it official.  (That will let us simplify some bits of the build,
    too, since they won't have to be conditional on Python anymore, so I'm all
    in favor of this change.)
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
