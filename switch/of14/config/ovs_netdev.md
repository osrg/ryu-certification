---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
59acda7f-7ab9-48bf-95f8-c02b3799543b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 85bbb704-c464-4deb-b3ce-f307da86486d
controller          : [5ae30090-88c5-4f3c-a171-162abb5fb60d]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [365db391-5862-4ba1-9bde-62ba00b99c58, 59e8638f-6615-4ecb-9a34-5d09bda4771e, 8c718431-eb33-4a1d-91f7-389bf0b12b61, d49f64e0-01a6-43a9-b732-ca9e60d9b95d]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5ae30090-88c5-4f3c-a171-162abb5fb60d
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="757", sec_since_disconnect="4", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d49f64e0-01a6-43a9-b732-ca9e60d9b95d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [93f3ebb2-9e57-4cac-950a-e36c16edc96d]
name                : "br0"

_uuid               : 365db391-5862-4ba1-9bde-62ba00b99c58
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [06cbb75e-e92f-4c49-90c2-10ce1339bf69]
name                : "eth23"

_uuid               : 8c718431-eb33-4a1d-91f7-389bf0b12b61
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b710f9a6-b4fa-4a3a-9e8a-fe98ad176c5c]
name                : "eth21"

_uuid               : 59e8638f-6615-4ecb-9a34-5d09bda4771e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [73d5e383-d02d-4ab7-8493-f62944c83665]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : b710f9a6-b4fa-4a3a-9e8a-fe98ad176c5c
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
statistics          : {collisions=0, rx_bytes=39365175395, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=26276480, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 93f3ebb2-9e57-4cac-950a-e36c16edc96d
admin_state         : down
duplex              : full
ifindex             : 593
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

_uuid               : 06cbb75e-e92f-4c49-90c2-10ce1339bf69
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4234357500, tx_dropped=0, tx_errors=0, tx_packets=2822905}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 73d5e383-d02d-4ab7-8493-f62944c83665
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=27875973790, tx_dropped=0, tx_errors=0, tx_packets=18598541}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e04f7e4f2f574500334326dbda1bb808cf25c721
Author:     Ciara Loftus &lt;ciara.loftus@intel.com&gt;
AuthorDate: Wed Oct 21 14:50:36 2015 +0100
Commit:     Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
CommitDate: Thu Oct 22 11:57:59 2015 -0700

    netdev-dpdk: Clean-up after vHost User port delete
    
    Unregister and delete the socket associated with a vhost-user
    port when the port is deleted and/or the switch is brought down.
    Do not delete the socket if the vhost-user device is still attached
    to the guest.
    
    Signed-off-by: Ciara Loftus &lt;ciara.loftus@intel.com&gt;
    Acked-by: Daniele Di Proietto &lt;diproiettod@vmware.com&gt;
</pre>
