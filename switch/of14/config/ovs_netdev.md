---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
66d3eda0-ecc0-4239-8cc8-a424f694e02b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 58ff1847-564c-4fd0-a2bd-2a8f9b0c5b63
controller          : [7a48c0bb-8922-460d-9331-ca58ca2eb5f3]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [457842af-0790-4b10-975e-848736b64c11, 968683c8-4263-43a9-8cdb-9b7ef6a04dda, a05081e3-d4f9-4ce0-a443-a7ca235bbcbe, de39fe48-0fc7-4a54-8975-ad7673bd7a89]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 7a48c0bb-8922-460d-9331-ca58ca2eb5f3
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="652", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : de39fe48-0fc7-4a54-8975-ad7673bd7a89
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a4049e9-8ee5-420d-802e-7817178ff500]
name                : "br0"

_uuid               : 968683c8-4263-43a9-8cdb-9b7ef6a04dda
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [76c8371b-2214-4395-939e-1001d6cd790d]
name                : "eth22"

_uuid               : a05081e3-d4f9-4ce0-a443-a7ca235bbcbe
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [34ee6751-57ef-4440-b9d2-37e16b749039]
name                : "eth23"

_uuid               : 457842af-0790-4b10-975e-848736b64c11
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2334fbc5-4f4f-4e68-b485-467a8d89ed75]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 2334fbc5-4f4f-4e68-b485-467a8d89ed75
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
statistics          : {collisions=0, rx_bytes=1192715632132, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=795487760, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0a4049e9-8ee5-420d-802e-7817178ff500
admin_state         : down
duplex              : full
ifindex             : 817
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

_uuid               : 34ee6751-57ef-4440-b9d2-37e16b749039
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=37510677000, tx_dropped=0, tx_errors=0, tx_packets=25007118}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 76c8371b-2214-4395-939e-1001d6cd790d
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=602493544544, tx_dropped=0, tx_errors=0, tx_packets=401812751}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4e5e44e30133939b792a013a812c84f564ffa8aa
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Mar 27 23:19:22 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Sat Mar 28 14:31:47 2015 -0700

    ofproto-dpif: Set need_revalidate when removing cfm from ofport.
    
    When cfm is deleted from a port, all modules should release their
    reference so that the cfm struct can be removed from the global hmap
    and freed.  Therein, the reference held by xlate module can only be
    released when the need_revalidate flag is set &#40;e.g set to
    REV_RECONFIGURE&#41;.  And this flag should be set while removing cfm
    from ofport.  Unfortunately, this has never been done before and the
    bug was hidden by another bug fixed in recent commit a190839
    &#40;netdev-vport: Do not update netdev when there is no config change.&#41;
    
    To fix this issue, this commit makes the code set need_revalidate
    when removing cfm from ofport.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
