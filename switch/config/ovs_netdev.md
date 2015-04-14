---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
f49fc8e0-3756-42a8-96c8-63f877724e8a
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
_uuid               : edadf0a4-e085-448f-bf34-69b8d94f6f40
controller          : [733deefa-2d2b-4848-8388-ab0120a4112c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [29562801-c21c-4b5f-b952-d0ea31482419, 3d8ce075-c3e8-4cee-9400-2125defb3371, ac106dc0-e02e-4bc9-a987-d09d16c053d1, fbe0f0dc-5942-47ec-a1c4-92e486f43e13]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 733deefa-2d2b-4848-8388-ab0120a4112c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="0", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : fbe0f0dc-5942-47ec-a1c4-92e486f43e13
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7ab29af8-1af8-43ad-b921-4d395999ff6a]
name                : "br0"

_uuid               : ac106dc0-e02e-4bc9-a987-d09d16c053d1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [74729b28-da8c-426a-912b-cfd37a962e2f]
name                : "eth21"

_uuid               : 29562801-c21c-4b5f-b952-d0ea31482419
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [70c7579c-3da9-4211-8e71-aafc52003811]
name                : "eth23"

_uuid               : 3d8ce075-c3e8-4cee-9400-2125defb3371
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0e3ced5b-090b-4f3e-8d5a-8713cca435c3]
name                : "eth22"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 7ab29af8-1af8-43ad-b921-4d395999ff6a
admin_state         : down
duplex              : full
ifindex             : 891
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

_uuid               : 74729b28-da8c-426a-912b-cfd37a962e2f
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
statistics          : {collisions=0, rx_bytes=1231374704686, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=821287494, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 70c7579c-3da9-4211-8e71-aafc52003811
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=40756725000, tx_dropped=0, tx_errors=0, tx_packets=27171150}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0e3ced5b-090b-4f3e-8d5a-8713cca435c3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630048804744, tx_dropped=0, tx_errors=0, tx_packets=420195773}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 77e2b03174d5e39eb99bcfba6fbc620402154674
Author:     Terry Wilson &lt;twilson@redhat.com&gt;
AuthorDate: Fri Apr 10 14:57:00 2015 -0500
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Tue Apr 14 09:28:57 2015 -0700

    python: Add setuptools for Python lib for PyPI.
    
    This adds very basic support for setuptools so that the OVS Python
    lib can be added to PyPI.
    
    This currently uses the Open vSwitch version number and the
    generated dirs.py, though there is no real reason to tie the
    Python libraries releases or version numbers to the main project's.
    
    Signed-off-by: Terry Wilson &lt;twilson@redhat.com&gt;
    Acked-by: Russell Bryant &lt;rbryant@redhat.com&gt;
    Acked-by: Kyle Mestery &lt;mestery@mestery.com&gt;
    [blp@nicira.com adjusted automake.mk]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
