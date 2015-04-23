---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fe0554d0-065c-4638-b0f0-21f7a8bf8a02
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
_uuid               : 28b690b1-ea43-49fa-a85d-13707933169f
controller          : [8477ce21-dc3e-45b9-9895-6e0d6ded876b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [578d7b4a-5e8f-4491-a0c9-30ff37641cc9, 5ff1b36e-57c9-4783-8cee-d65ad8827536, 6c701505-c944-40d9-8631-538864399503, fed1253f-891e-4dc7-a476-8578265dd5fd]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8477ce21-dc3e-45b9-9895-6e0d6ded876b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="647", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6c701505-c944-40d9-8631-538864399503
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [831ad4fb-0c5e-47a7-a88d-a3db9eab1dbb]
name                : "eth21"

_uuid               : 578d7b4a-5e8f-4491-a0c9-30ff37641cc9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0d3b9ad0-c657-45c6-a275-5acdcde0379c]
name                : "br0"

_uuid               : 5ff1b36e-57c9-4783-8cee-d65ad8827536
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b340c6e6-129f-4471-8474-ae6214af30eb]
name                : "eth22"

_uuid               : fed1253f-891e-4dc7-a476-8578265dd5fd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6ae884ac-bf98-4866-9cc5-ddc3d2872c82]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ae884ac-bf98-4866-9cc5-ddc3d2872c82
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=42773835000, tx_dropped=0, tx_errors=0, tx_packets=28515890}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0d3b9ad0-c657-45c6-a275-5acdcde0379c
admin_state         : down
duplex              : full
ifindex             : 937
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

_uuid               : b340c6e6-129f-4471-8474-ae6214af30eb
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631258134115, tx_dropped=0, tx_errors=0, tx_packets=421008988}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 831ad4fb-0c5e-47a7-a88d-a3db9eab1dbb
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
statistics          : {collisions=0, rx_bytes=1234063728661, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=823094953, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit e1e29b268c77c862f2827beeb4f319396dc66ef2
Author:     Nithin Raju &lt;nithin@vmware.com&gt;
AuthorDate: Wed Apr 22 17:10:10 2015 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Apr 23 11:01:38 2015 -0700

    datapath-windows: don't free switch cxt until ref == 0
    
    This is a hard to hit corner case, because currently we recommend that
    all handles to the kernel datapath be closed before trying to unload the
    OVS extension.
    
    Signed-off-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Acked-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
