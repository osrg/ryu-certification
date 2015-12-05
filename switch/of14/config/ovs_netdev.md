---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ac69f704-973c-4f89-b3f9-3d11b9003180
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ba93a5f4-0ba0-4298-9fbb-8914e59385dc
controller          : [deddd95a-e808-4667-8de1-292188ed63ed]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0dd1f15a-1c6a-48eb-b8e5-38b78455f121, 32e24d3c-7d10-4645-89df-95bfd0bc8c9c, 49a573c7-9aa5-4854-bda1-4adb3202ebec, 54c23a92-93e7-4133-8bb2-ffee1dc0c95f]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : deddd95a-e808-4667-8de1-292188ed63ed
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 32e24d3c-7d10-4645-89df-95bfd0bc8c9c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [85f639cc-0707-4bd9-a59f-19f814aefe64]
name                : "br0"

_uuid               : 0dd1f15a-1c6a-48eb-b8e5-38b78455f121
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0b34c018-39d5-4b2c-a39a-9f6d06253320]
name                : "eth21"

_uuid               : 54c23a92-93e7-4133-8bb2-ffee1dc0c95f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [21d53e2a-123f-4ced-905d-d6a76613faa3]
name                : "eth22"

_uuid               : 49a573c7-9aa5-4854-bda1-4adb3202ebec
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b51c5b4d-ba09-4f91-82c3-b9fdb137aa81]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 85f639cc-0707-4bd9-a59f-19f814aefe64
admin_state         : down
duplex              : full
ifindex             : 654
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

_uuid               : 0b34c018-39d5-4b2c-a39a-9f6d06253320
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
statistics          : {collisions=0, rx_bytes=41576817873, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27763004, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b51c5b4d-ba09-4f91-82c3-b9fdb137aa81
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=5854765500, tx_dropped=0, tx_errors=0, tx_packets=3903177}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 21d53e2a-123f-4ced-905d-d6a76613faa3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=28908700415, tx_dropped=0, tx_errors=0, tx_packets=19292447}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 7b27258c4e0821ade73e0e0a9bd5339328489523
Author:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
AuthorDate: Fri Dec 4 15:01:37 2015 -0800
Commit:     Jarno Rajahalme &lt;jarno@ovn.org&gt;
CommitDate: Fri Dec 4 15:01:37 2015 -0800

    ofproto-dpif: Validate NAT action support.
    
    The NAT validation is similar &#40;and based on&#41; the existing conntrack
    validation: when a dpif backer is created, we try to install a flow with
    the ct_state NAT bits set.  If the flow setup fails we assume that the
    backer doesn't support NAT and we reject OpenFlow flows with a NAT
    action or a match on the ct_state NAT bits.
    
    Signed-off-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
