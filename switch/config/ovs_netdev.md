---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e5f6329b-7add-4392-959f-398b1b6a26a8
    Bridge "br0"
        Controller "tcp:10.24.150.30"
        fail_mode: secure
        Port "eth7"
            Interface "eth7"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth8"
            Interface "eth8"

$ sudo ovs-vsctl list Bridge
_uuid               : 90505b46-4a4c-4b90-aa66-a69a93fa5e9d
controller          : [08ceba2f-d43b-4714-839d-5321f4ce02af]
datapath_id         : "0000000000000001"
datapath_type       : netdev
fail_mode           : secure
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [329ca1cd-4ef5-48f6-b203-3de820ca6c82, 62aadddd-f8e4-4ebb-8d42-6441cea1370a, 9a5a0337-9dc7-4e9a-8439-91ba30e41430]
protocols           : ["OpenFlow13"]
stp_enable          : false

$ sudo ovs-vsctl list Controller
_uuid               : 08ceba2f-d43b-4714-839d-5321f4ce02af
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="297", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30"

$ sudo ovs-vsctl list Port
_uuid               : 329ca1cd-4ef5-48f6-b203-3de820ca6c82
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d2dadd39-cc90-4859-8279-6b0bce58315d]
name                : "eth7"

_uuid               : 62aadddd-f8e4-4ebb-8d42-6441cea1370a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4b8a6c9e-640a-4a81-8261-407662ae8703]
name                : "br0"

_uuid               : 9a5a0337-9dc7-4e9a-8439-91ba30e41430
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c761aaa5-bbe0-4cd1-a764-e3ecb0b08516]
name                : "eth8"

$ sudo ovs-vsctl list Interface
_uuid               : d2dadd39-cc90-4859-8279-6b0bce58315d
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1550
name                : "eth7"
ofport              : 1
statistics          : {collisions=0, rx_bytes=2725451, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27682, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : c761aaa5-bbe0-4cd1-a764-e3ecb0b08516
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:ec"
mtu                 : 1550
name                : "eth8"
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=911924, tx_dropped=0, tx_errors=0, tx_packets=9834}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="3.10-0"}
type                : ""

_uuid               : 4b8a6c9e-640a-4a81-8261-407662ae8703
admin_state         : up
duplex              : full
ifindex             : 121
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : "00:60:e0:4a:84:eb"
mtu                 : 1500
name                : "br0"
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version="1.6", firmware_version="N/A"}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 6c3eee823e95d13c613935f0252c8a523bc6ef20
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Dec 27 17:00:30 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Wed Jan 8 17:13:32 2014 -0800

    dpif-netdev: Use separate threads for forwarding.
    
    For now, we use exactly two threads.  Presumably at some point we will want
    to make this configurable.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
