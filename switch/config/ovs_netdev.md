---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
59316edb-85db-49d8-9f79-966f535cd0d7
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
_uuid               : 8d00d6c5-c819-4e39-9eae-5adef335df4b
controller          : [a22c439d-a324-48a5-bec4-7f260c2e5028]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [6773f64f-f3f9-49a7-9af6-944f78b4550d, 72a296bf-ea8f-407d-92cd-312c05d8663b, 7bb1d6e0-4204-4bca-ac4b-4873a6cf160f, d6565849-e395-4812-92ce-364418df4767]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : a22c439d-a324-48a5-bec4-7f260c2e5028
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="661", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7bb1d6e0-4204-4bca-ac4b-4873a6cf160f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c960fda7-5c51-4206-912c-b0bbb6087677]
name                : "eth21"

_uuid               : d6565849-e395-4812-92ce-364418df4767
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ea6d7f7b-0616-452b-86a2-bfaa00c4a752]
name                : "eth23"

_uuid               : 6773f64f-f3f9-49a7-9af6-944f78b4550d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c8057bec-bc5a-4f75-9cf1-602538643b31]
name                : "br0"

_uuid               : 72a296bf-ea8f-407d-92cd-312c05d8663b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4f27c10a-1529-4130-808e-8b9a90800239]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c8057bec-bc5a-4f75-9cf1-602538643b31
admin_state         : down
duplex              : full
ifindex             : 744
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

_uuid               : 4f27c10a-1529-4130-808e-8b9a90800239
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=30172532333, tx_dropped=0, tx_errors=0, tx_packets=20142691}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c960fda7-5c51-4206-912c-b0bbb6087677
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
statistics          : {collisions=0, rx_bytes=44385285483, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=29651093, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ea6d7f7b-0616-452b-86a2-bfaa00c4a752
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7960014000, tx_dropped=0, tx_errors=0, tx_packets=5306676}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 72eaa2baa910ba41ed29b56617bffbc46bafc342
Author:     Ilya Maximets &lt;i.maximets@samsung.com&gt;
AuthorDate: Fri Jan 29 12:20:13 2016 +0300
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Fri Jan 29 07:46:24 2016 -0500

    ovn: Remove top ovn directory from PATHs.
    
    Since 5b5c922b0ca6 &#40;&quot;ovn-nbctl: Move ovn-nbctl to utilities directory.&quot;&#41;
    there is no more executables in top ovn directory.
    
    Removing of this directory from PATHs helps to avoid problems when
    old executable ./ovn/ovn-nbctl used instead of ./ovn/utilities/ovn-nbctl.
    
    This may happen if source directory was updated to commit 5b5c922b0ca6
    without calling 'make clean'.
    
    Fixes: 5b5c922b0ca6 &#40;&quot;ovn-nbctl: Move ovn-nbctl to utilities directory.&quot;&#41;
    Signed-off-by: Ilya Maximets &lt;i.maximets@samsung.com&gt;
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
</pre>
