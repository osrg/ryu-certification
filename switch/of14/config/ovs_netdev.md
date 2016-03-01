---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
92da9ae1-af22-42c3-ade2-97cb9dd0b317
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a29becd6-7d36-456d-9418-cc05ee960186
controller          : [8a37eb29-5d8f-4301-a53e-0e1453ba6790]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [08b79f10-17e7-44a7-b21c-170ee13b40be, 0fbd6f1a-e364-4577-a3a3-48e44b9b810a, 4f4ff3cc-8736-46af-bd63-6c6ff58cf833, e3a8a576-0195-4164-b1de-a4ad65ba96d2]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8a37eb29-5d8f-4301-a53e-0e1453ba6790
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="11", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 4f4ff3cc-8736-46af-bd63-6c6ff58cf833
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5dcaa765-bf13-4281-b6a7-faf172e5b583]
name                : "eth22"

_uuid               : 08b79f10-17e7-44a7-b21c-170ee13b40be
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [961dce81-016d-46b9-8a0c-1ecfa864a179]
name                : "br0"

_uuid               : 0fbd6f1a-e364-4577-a3a3-48e44b9b810a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [eecb081f-ff36-40e1-b737-398d8a50185c]
name                : "eth23"

_uuid               : e3a8a576-0195-4164-b1de-a4ad65ba96d2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [75dfcf5c-e98e-4197-ae26-335cba021c59]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 75dfcf5c-e98e-4197-ae26-335cba021c59
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
statistics          : {collisions=0, rx_bytes=47427673907, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31696456, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 961dce81-016d-46b9-8a0c-1ecfa864a179
admin_state         : down
duplex              : full
ifindex             : 850
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

_uuid               : 5dcaa765-bf13-4281-b6a7-faf172e5b583
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31542354549, tx_dropped=0, tx_errors=0, tx_packets=21064248}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : eecb081f-ff36-40e1-b737-398d8a50185c
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=10239885000, tx_dropped=0, tx_errors=0, tx_packets=6826590}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d0a46cb4608e632f5028034762f0adde2ce947a0
Author:     Russell Bryant &lt;russell@ovn.org&gt;
AuthorDate: Mon Feb 29 15:51:57 2016 -0500
Commit:     Russell Bryant &lt;russell@ovn.org&gt;
CommitDate: Tue Mar 1 11:55:00 2016 -0500

    ofpbuf: Fix trivial spelling typo.
    
    s/bofy/body/. I noticed this spelling typo while reading this header
    file.
    
    Signed-off-by: Russell Bryant &lt;russell@ovn.org&gt;
    Acked-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
