---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
12c75cc8-15a8-41e4-a040-dc66aa7d1f67
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : aeae9ad4-f6ba-4b77-8196-a12bb9b0a701
controller          : [e7887f88-be57-4077-bc1f-2e47e8fec019]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [0b546fd2-4e48-484e-bc38-d7b3b609be3a, 1e566693-ef3b-4ebd-bc0e-680d03862baa, b4599f5d-eeb2-4b4b-aacf-c3f0f1257fb7]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : e7887f88-be57-4077-bc1f-2e47e8fec019
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=927, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b4599f5d-eeb2-4b4b-aacf-c3f0f1257fb7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [62085ffb-8b61-4c38-bfbf-8112db999648]
name                : eth7

_uuid               : 0b546fd2-4e48-484e-bc38-d7b3b609be3a
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [1367420f-cafd-4c7a-afb3-cf83a6ce4953]
name                : eth8

_uuid               : 1e566693-ef3b-4ebd-bc0e-680d03862baa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4e22a24a-a9a2-48ce-b809-bb9a578af8f0]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4e22a24a-a9a2-48ce-b809-bb9a578af8f0
admin_state         : down
duplex              : full
ifindex             : 966
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 1367420f-cafd-4c7a-afb3-cf83a6ce4953
admin_state         : up
duplex              : full
ifindex             : 11
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:ec
mtu                 : 1550
name                : eth8
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7285952, tx_dropped=0, tx_errors=0, tx_packets=77663}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 62085ffb-8b61-4c38-bfbf-8112db999648
admin_state         : up
duplex              : full
ifindex             : 10
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : eth7
ofport              : 1
statistics          : {collisions=0, rx_bytes=3075340133, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72757822, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit bee83872cab0c76877de0d8d93847a03ddb10503
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Thu Apr 10 16:57:51 2014 +1200
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Apr 10 08:23:57 2014 -0700

    SubmittingPatches: Rename to CONTRIBUTING.
    
    This makes the GitHub interface aware of the contribution guidelines,
    so it will be displayed to contributors when they submit issues or pull
    requests.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
