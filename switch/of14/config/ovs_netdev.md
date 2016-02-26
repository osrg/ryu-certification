---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
036d7fdb-f491-4cdc-bc11-79a51fa1dad7
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : e2026062-eaf9-4777-b8cc-89cf2cb97afd
controller          : [cc119ff9-716c-4329-8f1a-f4ce65b1f0e5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [09f4ad5b-a905-4100-ae8d-fd4227147c4d, 0fff9afe-3cb8-4ccb-8428-254f54aa9858, 67dc01c8-9306-4d5c-b6f1-6ee2e4bca085, c9058c2c-2480-4b87-bc1d-f63edbebeda8]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : cc119ff9-716c-4329-8f1a-f4ce65b1f0e5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="12", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c9058c2c-2480-4b87-bc1d-f63edbebeda8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9f9afcb2-fa19-4346-b01b-46b6c6cf7ebd]
name                : "eth22"

_uuid               : 67dc01c8-9306-4d5c-b6f1-6ee2e4bca085
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ef54cdfc-def3-4a85-bb72-da85ed7fa0f3]
name                : "eth21"

_uuid               : 0fff9afe-3cb8-4ccb-8428-254f54aa9858
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7b17cd7a-f19d-4464-86dc-6f3539adb67a]
name                : "br0"

_uuid               : 09f4ad5b-a905-4100-ae8d-fd4227147c4d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d4e6f567-18f1-4208-8583-63aa28fe7ab9]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ef54cdfc-def3-4a85-bb72-da85ed7fa0f3
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
statistics          : {collisions=0, rx_bytes=47076615476, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31460441, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9f9afcb2-fa19-4346-b01b-46b6c6cf7ebd
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31383771642, tx_dropped=0, tx_errors=0, tx_packets=20957561}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 7b17cd7a-f19d-4464-86dc-6f3539adb67a
admin_state         : down
duplex              : full
ifindex             : 836
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

_uuid               : d4e6f567-18f1-4208-8583-63aa28fe7ab9
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9977338500, tx_dropped=0, tx_errors=0, tx_packets=6651559}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 92f9822b0d9454540b710e5818e4a058ff663ce7
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Thu Feb 25 14:24:20 2016 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Fri Feb 26 12:50:49 2016 -0800

    tests: Fix use of &quot;test&quot;.
    
    Only = is portable for testing equality, == is a nonportable extension.
    
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
