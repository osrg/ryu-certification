---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b0eacbea-ad45-4541-96c9-8a298020ef00
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
_uuid               : b26880ae-838f-4e23-b303-f51af2e40608
controller          : [267ce725-35a8-4862-9d00-3c390938d29c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [06c05641-5759-4841-b4ea-c0bce25dce60, 9452b5b4-001d-46a2-9dfe-226ce00caec8, cba605fe-432e-42a1-a644-46bb5086aa79]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 267ce725-35a8-4862-9d00-3c390938d29c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=376, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9452b5b4-001d-46a2-9dfe-226ce00caec8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5c3cd4f9-abaf-41bb-8626-b87da0888152]
name                : eth7

_uuid               : 06c05641-5759-4841-b4ea-c0bce25dce60
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b2234e85-df3a-46a1-a2ce-977233688c4f]
name                : eth8

_uuid               : cba605fe-432e-42a1-a644-46bb5086aa79
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0369bb7d-db15-4668-b290-eac19c6b474e]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 0369bb7d-db15-4668-b290-eac19c6b474e
admin_state         : up
duplex              : full
ifindex             : 383
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

_uuid               : 5c3cd4f9-abaf-41bb-8626-b87da0888152
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
statistics          : {collisions=0, rx_bytes=3060814747, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72610402, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : b2234e85-df3a-46a1-a2ce-977233688c4f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2991696, tx_dropped=0, tx_errors=0, tx_packets=31929}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3b401f9baf4c0dd9e9eebb0a9f4417fdf3a80774
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu Feb 27 11:18:31 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Feb 27 11:19:01 2014 -0800

    tests: Re-fix a race.
    
    Patch bf06c4fe (tests/ofproto-dpif.at: Workaround a race.), fixed a
    race condition which patch 0a8763f (ofproto-dpif-upcall: Hardcode
    max_idle to 1500ms.) unfixed.
    
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Reported-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
