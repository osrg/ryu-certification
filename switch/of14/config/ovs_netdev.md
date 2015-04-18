---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3388ee9e-bac5-40fe-917c-abb7edf8dbe9
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 476c2d79-1a76-49ea-9582-6a875a1dd74f
controller          : [61c06c27-4249-4149-b398-693af3ca98af]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [1920e2cc-3bbf-47de-bcc6-ce320aa606e3, 2e453764-fd9f-4424-a4f3-f8c30cff5454, 6596808c-9f42-4bdf-a84a-dc7fd18c5a59, fdd368a4-26af-4875-bc45-04f36d19cb83]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 61c06c27-4249-4149-b398-693af3ca98af
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 2e453764-fd9f-4424-a4f3-f8c30cff5454
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [48893762-0c89-4e29-a10f-fe42b5ff2162]
name                : "eth22"

_uuid               : 1920e2cc-3bbf-47de-bcc6-ce320aa606e3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ea66b94f-39f0-4b05-9de9-3ca2cfd5add6]
name                : "eth23"

_uuid               : fdd368a4-26af-4875-bc45-04f36d19cb83
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b4cfdb2c-6aae-49e4-b014-683b62f21c42]
name                : "br0"

_uuid               : 6596808c-9f42-4bdf-a84a-dc7fd18c5a59
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0cb3aa83-9c88-464a-abe7-8d58fc1cd561]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b4cfdb2c-6aae-49e4-b014-683b62f21c42
admin_state         : down
duplex              : full
ifindex             : 921
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

_uuid               : 48893762-0c89-4e29-a10f-fe42b5ff2162
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630836992899, tx_dropped=0, tx_errors=0, tx_packets=420725794}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ea66b94f-39f0-4b05-9de9-3ca2cfd5add6
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=42072708000, tx_dropped=0, tx_errors=0, tx_packets=28048472}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0cb3aa83-9c88-464a-abe7-8d58fc1cd561
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
statistics          : {collisions=0, rx_bytes=1233128404561, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=822466264, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f315ae4f469a44c3691057b541425da4d4f9cbdf
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Apr 17 11:30:18 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Sat Apr 18 00:56:18 2015 -0700

    dkms.conf.in: Install all kernel modules.
    
    With the latest change of separating vports into their own modules,
    we need to update the dkms.conf.in and make dkms install all vport
    modules.  So, this commit modifies the debian/rules to read all
    kernel module names and sets the dkms.conf correctly.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
