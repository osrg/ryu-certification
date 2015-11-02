---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
15616d82-bf0d-4f60-b69f-c49c4bf47f16
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ccfb6886-1cc1-4601-8b95-6d892b68a184
controller          : [523ba05d-5142-465e-acf7-c66dc6e4ed3a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [36a1643d-b528-4a50-816c-c70d058fc167, 60c34eab-5e99-4ff6-8868-47122191f20b, 6ead3ebc-4ecb-420c-ae8c-85a247fb8067, 9f18c7c3-d215-4a06-87c5-fb9e3f89bb4a]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 523ba05d-5142-465e-acf7-c66dc6e4ed3a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="767", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ead3ebc-4ecb-420c-ae8c-85a247fb8067
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a402bbe0-b37d-4bf2-96be-4611a8a96b3f]
name                : "br0"

_uuid               : 36a1643d-b528-4a50-816c-c70d058fc167
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [93d8beb4-fc68-47e1-8dae-9361fe241811]
name                : "eth23"

_uuid               : 60c34eab-5e99-4ff6-8868-47122191f20b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fbb40cd7-e3ec-412a-b193-4497774478c7]
name                : "eth21"

_uuid               : 9f18c7c3-d215-4a06-87c5-fb9e3f89bb4a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e4ab6ed2-0ebf-4f54-8811-16db8e35430f]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 93d8beb4-fc68-47e1-8dae-9361fe241811
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5e"
mtu                 : 1550
name                : "eth23"
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4935667500, tx_dropped=0, tx_errors=0, tx_packets=3290445}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : a402bbe0-b37d-4bf2-96be-4611a8a96b3f
admin_state         : down
duplex              : full
ifindex             : 611
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal

_uuid               : e4ab6ed2-0ebf-4f54-8811-16db8e35430f
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5d"
mtu                 : 1550
name                : "eth22"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28297710472, tx_dropped=0, tx_errors=0, tx_packets=18881906}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : fbb40cd7-e3ec-412a-b193-4497774478c7
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:56:53:5c"
mtu                 : 1550
name                : "eth21"
ofport              : 1
statistics          : {collisions=0, rx_bytes=40301342365, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26905743, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 2f83a90542c9029165955a2574241f07e3016bfc
Author:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
AuthorDate: Mon Nov 2 14:17:14 2015 +0530
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Mon Nov 2 09:37:49 2015 -0800

    travis: Update target kernel list.
    
    Update the kernel list to sync with stable kernels from kernel.org
    
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
