---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
5b47b1b9-7822-44a8-a60d-9c4ee9d9a53c
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : dcda8cec-926b-4655-9d01-8bf62cabecec
controller          : [f2b24a40-7f0b-496b-a8be-8c5801fcddcd]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [58a7f20e-e0b7-406e-86bc-9a0f7efa7d2b, 7703fd5c-774f-4752-975e-4c09f3aa78cb, c2f9dd82-bc06-40fb-b5cb-e8ee077959a3, fcd138e9-b61f-4722-96b4-0af20bc87cb3]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : f2b24a40-7f0b-496b-a8be-8c5801fcddcd
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7703fd5c-774f-4752-975e-4c09f3aa78cb
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [81f2f609-2ae0-4f86-8e2a-9a59e6344996]
name                : "eth23"

_uuid               : fcd138e9-b61f-4722-96b4-0af20bc87cb3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [30a0620f-1264-4726-8ce7-7c51eae1790a]
name                : "eth22"

_uuid               : 58a7f20e-e0b7-406e-86bc-9a0f7efa7d2b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [04ef3f01-eebf-48e7-8fc9-8d4b9ffadd59]
name                : "br0"

_uuid               : c2f9dd82-bc06-40fb-b5cb-e8ee077959a3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7f45c8d8-d1b3-4410-bce8-0be2d5a9ed48]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7f45c8d8-d1b3-4410-bce8-0be2d5a9ed48
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 81f2f609-2ae0-4f86-8e2a-9a59e6344996
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 04ef3f01-eebf-48e7-8fc9-8d4b9ffadd59
admin_state         : down
duplex              : full
ifindex             : 353
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

_uuid               : 30a0620f-1264-4726-8ce7-7c51eae1790a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 600a8085e27f00a538e1abd14128606c67fcc7e1
Author:     Flavio Leitner &lt;fbl@redhat.com&gt;
AuthorDate: Thu Aug 13 16:06:29 2015 -0300
Commit:     Justin Pettit &lt;jpettit@nicira.com&gt;
CommitDate: Fri Aug 14 09:37:59 2015 -0700

    rhel: add installed but not packaged OVN tools
    
    This patch adds the following to OVN %files:
       /usr/bin/ovn-controller-vtep
       /usr/bin/ovn-sbctl
       /usr/share/man/man8/ovn-controller-vtep.8.gz
       /usr/share/man/man8/ovn-sbctl.8.gz
    
    Signed-off-by: Flavio Leitner &lt;fbl@redhat.com&gt;
    Signed-off-by: Justin Pettit &lt;jpettit@nicira.com&gt;
    Acked-by: Russell Bryant &lt;rbryant@redhat.com&gt;
</pre>
