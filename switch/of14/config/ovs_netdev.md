---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c6c4c7ee-9195-401c-9fbb-58b63f477a23
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
_uuid               : 8f18f6d4-59b4-47bb-9edc-192aebeacb97
controller          : [0b00962c-f1f4-4031-9202-f3f1652e5d5b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3baa2c19-b76b-4bb1-9540-37a72a9956de, 6787ca1a-f295-4270-b432-d51293362589, 868342cf-89fc-4d42-8a3b-9a1597b8c2cf, a2aa5213-6836-475c-8867-adb00d0c411c]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 0b00962c-f1f4-4031-9202-f3f1652e5d5b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="656", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 3baa2c19-b76b-4bb1-9540-37a72a9956de
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b4aa2f0f-43c3-4472-87d4-47676fe5a6eb]
name                : "eth22"

_uuid               : 6787ca1a-f295-4270-b432-d51293362589
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fd03c357-ee8c-47cf-bbd2-b950b60323df]
name                : "eth23"

_uuid               : 868342cf-89fc-4d42-8a3b-9a1597b8c2cf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ddb8b5a1-a742-48fb-8cf8-8da2074b689a]
name                : "eth21"

_uuid               : a2aa5213-6836-475c-8867-adb00d0c411c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3e23b9fb-6c0b-46f4-8519-adcc06ef0cf9]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ddb8b5a1-a742-48fb-8cf8-8da2074b689a
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
statistics          : {collisions=0, rx_bytes=1217924176527, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=812307731, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : fd03c357-ee8c-47cf-bbd2-b950b60323df
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=39178008000, tx_dropped=0, tx_errors=0, tx_packets=26118672}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3e23b9fb-6c0b-46f4-8519-adcc06ef0cf9
admin_state         : down
duplex              : full
ifindex             : 854
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

_uuid               : b4aa2f0f-43c3-4472-87d4-47676fe5a6eb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=619501525053, tx_dropped=0, tx_errors=0, tx_packets=413158415}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4f7e5c274bfff6187313588a66491bcf45b7a709
Author:     Russell Bryant &lt;rbryant@redhat.com&gt;
AuthorDate: Thu Apr 2 17:51:49 2015 -0400
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Apr 2 19:15:52 2015 -0700

    INSTALL.md: Add note about EXTRA_CFLAGS.
    
    Add a note about the use of EXTRA_CFLAGS to provide custom CFLAGS for
    the build of the Linux kernel module.
    
    This addition is technically in the &quot;configuring the sources&quot; section
    of the document.  However, it's the spot where custom CFLAGS is
    discussed already, so that seemed like the best place to put it.
    Alternatively, it could go in the &quot;Building the Sources&quot; section
    instead.
    
    Signed-off-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
