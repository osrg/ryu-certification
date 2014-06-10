---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cb4bfb97-c01e-4562-8ace-e6b48e04c9cf
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 2fedb25e-5c0d-41a6-b63c-0f7d4631882c
controller          : [4e6862cd-646f-431b-baa4-aa52083d01d6]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [7c8c97f5-7fa6-4cfb-87ef-990c246510ce, 849a87fd-2196-4dc7-bbb7-f158cc85657e, b537f68f-f9e6-4da9-a56d-c04ffa753ace, f09eab11-f26b-432c-bc32-5b5aeb67a94a]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 4e6862cd-646f-431b-baa4-aa52083d01d6
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=966, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f09eab11-f26b-432c-bc32-5b5aeb67a94a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [21a69070-6c3f-44e1-9900-7e81e3ffff95]
name                : br0

_uuid               : 849a87fd-2196-4dc7-bbb7-f158cc85657e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d1f8d0b-0a3b-49a3-826e-85777902f8c9]
name                : eth23

_uuid               : 7c8c97f5-7fa6-4cfb-87ef-990c246510ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6a233295-10e1-414c-af2d-99c80275c06c]
name                : eth22

_uuid               : b537f68f-f9e6-4da9-a56d-c04ffa753ace
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [14b2e645-703d-4d41-981a-4fca7ddfa729]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 21a69070-6c3f-44e1-9900-7e81e3ffff95
admin_state         : down
duplex              : full
ifindex             : 428
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

_uuid               : 6a233295-10e1-414c-af2d-99c80275c06c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1246056928, tx_dropped=0, tx_errors=0, tx_packets=12307567}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 14b2e645-703d-4d41-981a-4fca7ddfa729
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
statistics          : {collisions=0, rx_bytes=428629731, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26120600, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3d1f8d0b-0a3b-49a3-826e-85777902f8c9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1515953908, tx_dropped=0, tx_errors=0, tx_packets=6737259}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c2cbb53c0f041f38f1f22673adf379a0e6a8176e
Author:     Polehn, Mike A &lt;mike.a.polehn@intel.com&gt;
AuthorDate: Mon Jun 9 14:47:05 2014 +0000
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Tue Jun 10 13:23:32 2014 -0700

    INSTALL.DPDK: User space dpdk setup documentation addition.
    
    Added details of dpdk poll mode setup to make it easier
    for someone, not familiar, to get it operating.
    
    Signed-off-by: Mike A. Polehn &lt;mike.a.polehn@intel.com&gt;
    Signed-off-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
