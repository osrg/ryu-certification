---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
085f643d-6975-449b-96d2-2a466b985242
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : f24e5f1d-8c7b-417c-aa72-8774af16ebac
controller          : [e228404d-bff3-4058-a703-ec8f0564fad8]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0e2cac90-339b-4f84-af2c-45b13245f8cb, 4e229f23-0e7c-4f59-a2e5-6d187b9aa6fa, d574e130-e789-44ed-94e4-bf6793576d3b, dc04eefd-f0ec-4140-99af-92e17e8731c8]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e228404d-bff3-4058-a703-ec8f0564fad8
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="646", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0e2cac90-339b-4f84-af2c-45b13245f8cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3b57f4bf-9d6d-4421-868b-03223c29c39c]
name                : "eth22"

_uuid               : d574e130-e789-44ed-94e4-bf6793576d3b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7aae1476-bde4-47ad-af88-310a3d38103e]
name                : "eth21"

_uuid               : dc04eefd-f0ec-4140-99af-92e17e8731c8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c76adba4-a961-4db7-941d-9e89c785c19f]
name                : "br0"

_uuid               : 4e229f23-0e7c-4f59-a2e5-6d187b9aa6fa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [974f7548-24ee-4762-bbd9-95e3a66a2218]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c76adba4-a961-4db7-941d-9e89c785c19f
admin_state         : down
duplex              : full
ifindex             : 957
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

_uuid               : 974f7548-24ee-4762-bbd9-95e3a66a2218
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=43650868500, tx_dropped=0, tx_errors=0, tx_packets=29100579}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7aae1476-bde4-47ad-af88-310a3d38103e
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
statistics          : {collisions=0, rx_bytes=1235232755911, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=823880729, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3b57f4bf-9d6d-4421-868b-03223c29c39c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631783778385, tx_dropped=0, tx_errors=0, tx_packets=421362459}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1aa2bf92505da27320b37b53244fb9715062ab04
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Wed Apr 29 10:41:39 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Wed Apr 29 13:46:32 2015 -0700

    test-ovsdb: Fix conditional statement.
    
    Old version of python does not support the following conditional
    statement syntax in one assignment:
    
       var = value1 if cond else value2
    
    This commit fixes it by convert it back to use two assignments.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Russell Bryant &lt;rbryant@redhat.com&gt;
</pre>
