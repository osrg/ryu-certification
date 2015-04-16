---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
cbc9cd8f-f66e-44b6-bb7b-9beae2a06171
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 8e4dbb85-b4d6-4b7f-99d4-699e7dfd9540
controller          : [8c0188c5-3b22-4166-bbae-ccf6875e1210]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [07306099-4382-42fb-b2e5-3f7325d4a572, 764ab223-64a7-4dcd-9d3c-0e047882022a, e98079ff-c0dd-4a31-917b-152c16b481b3, f7b13d5f-83b9-4e84-aa2d-9d98f5b8e754]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8c0188c5-3b22-4166-bbae-ccf6875e1210
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="647", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 07306099-4382-42fb-b2e5-3f7325d4a572
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ab6672cb-ba69-4831-bf0f-06f8bcf7d752]
name                : "br0"

_uuid               : e98079ff-c0dd-4a31-917b-152c16b481b3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6d639838-125c-4af2-9ea5-2b32750d34a1]
name                : "eth23"

_uuid               : f7b13d5f-83b9-4e84-aa2d-9d98f5b8e754
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d74777a6-4275-4f83-b7f2-a120d77d5a38]
name                : "eth22"

_uuid               : 764ab223-64a7-4dcd-9d3c-0e047882022a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [10f3d207-a6ca-43b0-a82f-6455b6305fe4]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6d639838-125c-4af2-9ea5-2b32750d34a1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=41458419000, tx_dropped=0, tx_errors=0, tx_packets=27638946}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : d74777a6-4275-4f83-b7f2-a120d77d5a38
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630469368460, tx_dropped=0, tx_errors=0, tx_packets=420478582}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ab6672cb-ba69-4831-bf0f-06f8bcf7d752
admin_state         : down
duplex              : full
ifindex             : 907
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

_uuid               : 10f3d207-a6ca-43b0-a82f-6455b6305fe4
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
statistics          : {collisions=0, rx_bytes=1232310037786, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=821916189, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit f097013adabf50cf8d82562f0893d60999294bba
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Wed Apr 15 17:10:50 2015 +0900
Commit:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
CommitDate: Thu Apr 16 15:08:48 2015 +0900

    run-ryu: Use the IANA OpenFlow port number
    
    Specify the use of the port 6653 for ryu side explicitly
    because it still defaults to port 6633.
    
    Fixes check-ryu after commit d4763d1d4efbbcfd884df2d668980d61ec89d75a.
    &#40;&quot;Use the IANA-assigned ports for OpenFlow and OVSDB.&quot;&#41;
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
