---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
e94c66ca-01ca-4407-8912-7c0ec0bbc083
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : beaef386-ef70-46d1-b398-4a554f4ab0b5
controller          : [bff79a39-c2ff-45ac-8405-72aeb4eb91a1]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [5ca1bc00-e762-415e-a190-df7a8dbe9ba3, 71ef636c-c6ff-425d-ae1e-631fae00cc78, bf86fdcc-5d20-477c-8bee-0a871ace0b72, fdd8046b-f0d3-4b22-8890-d77bd85d8c90]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bff79a39-c2ff-45ac-8405-72aeb4eb91a1
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="666", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 5ca1bc00-e762-415e-a190-df7a8dbe9ba3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [59e8d5cb-f72d-44a6-a5bf-97ae4762ead9]
name                : "eth23"

_uuid               : bf86fdcc-5d20-477c-8bee-0a871ace0b72
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [54554b69-9e0a-4b60-82e0-69e00e7b0b0a]
name                : "eth22"

_uuid               : 71ef636c-c6ff-425d-ae1e-631fae00cc78
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0bd1bd32-01bc-4612-9946-cbae6d18a2f3]
name                : "eth21"

_uuid               : fdd8046b-f0d3-4b22-8890-d77bd85d8c90
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c666e6c5-5f78-4f8d-aaa4-cdf79ab05b28]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 54554b69-9e0a-4b60-82e0-69e00e7b0b0a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29908978918, tx_dropped=0, tx_errors=0, tx_packets=19965385}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c666e6c5-5f78-4f8d-aaa4-cdf79ab05b28
admin_state         : down
duplex              : full
ifindex             : 724
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

_uuid               : 0bd1bd32-01bc-4612-9946-cbae6d18a2f3
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
statistics          : {collisions=0, rx_bytes=43800178528, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29257733, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 59e8d5cb-f72d-44a6-a5bf-97ae4762ead9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7521670500, tx_dropped=0, tx_errors=0, tx_packets=5014447}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 03756304cf67a4f241ea124696ab0dbf40d9d679
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Wed Jan 6 15:23:08 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Fri Jan 22 08:25:27 2016 -0500

    python: Remove old style classes.
    
    Python 3 removed support for &quot;old-style classes&quot;.  Classes should always
    inherit from object to get consistent behavior between Python 2 and 3.
    
    Enable a flake8 warning to help prevent regressions in the future.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
