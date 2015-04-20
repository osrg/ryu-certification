---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fdde7ba5-b197-40b7-83f1-8502e6daf8d1
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : be68a298-6b92-4eec-810a-bbb50ba8bf22
controller          : [ef7ce03d-e25a-46d8-9f06-b7f44e5678a6]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [12733203-eaf2-4ef7-bb41-10fa61247b8f, 3c57ff10-2eec-4852-94e1-b3277b77a77b, 3e2bdf4b-dbc1-4363-b994-4dac1ab7b622, ffb4cea8-4e05-4e6a-a07a-1e81569980b8]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ef7ce03d-e25a-46d8-9f06-b7f44e5678a6
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="656", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ffb4cea8-4e05-4e6a-a07a-1e81569980b8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [17d4cdc7-71ea-4eb3-abab-39647628d137]
name                : "eth23"

_uuid               : 3c57ff10-2eec-4852-94e1-b3277b77a77b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d2752edc-d24f-43bf-869b-c3fa3bfead8d]
name                : "eth22"

_uuid               : 12733203-eaf2-4ef7-bb41-10fa61247b8f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d085b2d-78f7-4b55-bc13-8e283fe961a5]
name                : "br0"

_uuid               : 3e2bdf4b-dbc1-4363-b994-4dac1ab7b622
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [905a5697-cc58-41f2-a0d9-455af724183e]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : d2752edc-d24f-43bf-869b-c3fa3bfead8d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630889333676, tx_dropped=0, tx_errors=0, tx_packets=420760992}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3d085b2d-78f7-4b55-bc13-8e283fe961a5
admin_state         : down
duplex              : full
ifindex             : 923
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

_uuid               : 905a5697-cc58-41f2-a0d9-455af724183e
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
statistics          : {collisions=0, rx_bytes=1233245324386, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=822544853, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 17d4cdc7-71ea-4eb3-abab-39647628d137
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=42160653000, tx_dropped=0, tx_errors=0, tx_packets=28107102}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 513a32eea658ed86f3aaa3eda9f701d31d6fbcd6
Author:     Kevin Lo &lt;kevlo@FreeBSD.org&gt;
AuthorDate: Sun Apr 19 01:48:06 2015 +0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Apr 20 10:58:43 2015 -0700

    configure.ac: Fix pthread linking on FreeBSD.
    
    The configure script checks for the existence of pthread_sigmask.
    However, on FreeBSD, libc contains no-op stubs for many of the
    pthread_* functions.  As a result, the AC_SEARCH_LIBS macro returns
    &quot;none required&quot;.
    
    As an alternative to checking pthread_sigmask, a solution is to check
    pthread_create.
    
    Signed-off-by: Kevin Lo &lt;kevlo@FreeBSD.org&gt;
    Acked-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
