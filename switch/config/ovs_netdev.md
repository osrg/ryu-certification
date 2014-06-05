---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
99e62299-1e96-410e-8d0b-090bb142ec94
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : caee27f2-930f-4d85-a69b-3cb633f9145e
controller          : [66ac4e0c-8193-4780-9236-00eeced9c492]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [3243bf5a-05c0-4831-b52b-24cf983b41fe, 3830e83e-597f-4265-a4db-21994b799357, a17a758f-4acc-4404-be98-26f7f61a9503, c0241e73-d28e-4828-98cd-2575df2ac40c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 66ac4e0c-8193-4780-9236-00eeced9c492
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=962, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3830e83e-597f-4265-a4db-21994b799357
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [23a884b8-d6e8-4027-ac87-9b649f45bd2c]
name                : eth22

_uuid               : 3243bf5a-05c0-4831-b52b-24cf983b41fe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d125398a-30bb-4571-a722-9774746b689c]
name                : eth21

_uuid               : a17a758f-4acc-4404-be98-26f7f61a9503
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d18e4b5f-4baa-4832-8af2-12bc5f1fb32a]
name                : eth23

_uuid               : c0241e73-d28e-4828-98cd-2575df2ac40c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [331cb08c-5058-4d7f-b1d1-716317b52c3a]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 331cb08c-5058-4d7f-b1d1-716317b52c3a
admin_state         : down
duplex              : full
ifindex             : 392
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

_uuid               : 23a884b8-d6e8-4027-ac87-9b649f45bd2c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3842056148, tx_dropped=0, tx_errors=0, tx_packets=11172399}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d125398a-30bb-4571-a722-9774746b689c
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
statistics          : {collisions=0, rx_bytes=1231658721, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=23785646, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : d18e4b5f-4baa-4832-8af2-12bc5f1fb32a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=575122408, tx_dropped=0, tx_errors=0, tx_packets=6110038}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit ee088a75c65c5bc2a32887cde1c1ebc1c7fac232
Author:     Simon Horman &lt;horms@verge.net.au&gt;
AuthorDate: Thu Jun 5 18:54:47 2014 +0900
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Jun 5 13:08:59 2014 -0700

    ofproto: Send monitor updates if a flow mod changes a rules actions
    
    Without this change a monitor update will be sent when a flow mod changes
    a rules cookie but not if only the actions are updated. This appears
    to be a logic error.
    
    I noticed this while working on implementing OpenFlow1.4 flow monitor
    as an OpenFlow1.4 flow mod does not update a rules cookie.
    
    Signed-off-by: Simon Horman &lt;horms@verge.net.au&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
