---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d596f4a6-3dbe-45de-aad3-a86adfb929ac
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port br0
            Interface br0
                type: internal
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ed961b23-e9f3-4e49-b10a-39ef09d6d558
controller          : [b7a98c64-694f-4e97-85bb-dbfb8f159aba]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [02568469-d7fe-431b-9e07-54cf249e1875, 80904b96-2e6a-4717-a065-1a7b2c3fb982, a3286520-5d03-4411-8139-a1b5aed1b059, b20e61a3-0883-4f2b-a523-6b155e8041b8]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b7a98c64-694f-4e97-85bb-dbfb8f159aba
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=972, sec_since_disconnect=6, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a3286520-5d03-4411-8139-a1b5aed1b059
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fc69d1e8-2ecc-4cb1-8cde-fcef1eacf8a1]
name                : eth22

_uuid               : 02568469-d7fe-431b-9e07-54cf249e1875
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0e14e71e-76bd-4f7d-a287-785dfb1922ed]
name                : eth23

_uuid               : 80904b96-2e6a-4717-a065-1a7b2c3fb982
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a79fde52-1b32-47ef-85e0-8826c4cc752d]
name                : br0

_uuid               : b20e61a3-0883-4f2b-a523-6b155e8041b8
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [faa47912-d6c4-4477-ae6f-bd1f9be29e9c]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : fc69d1e8-2ecc-4cb1-8cde-fcef1eacf8a1
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1985864732, tx_dropped=0, tx_errors=0, tx_packets=12804604}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : faa47912-d6c4-4477-ae6f-bd1f9be29e9c
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=1963690576, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=27152958, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0e14e71e-76bd-4f7d-a287-785dfb1922ed
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2560204408, tx_dropped=0, tx_errors=0, tx_packets=7433426}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : a79fde52-1b32-47ef-85e0-8826c4cc752d
admin_state         : down
duplex              : full
ifindex             : 466
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit dad530c1208503c9e2aa264f88fedb31926f14b2
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Thu Jun 12 11:56:57 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Jun 12 12:52:51 2014 -0700

    test-jsonrpc: Add the ability to detach on Windows.
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
