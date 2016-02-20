---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
4481e709-7599-4e77-a07f-877a9e188026
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
_uuid               : 6c35b736-0207-4afc-bbd0-949a88427731
controller          : [c5c65207-d417-4638-8776-250c9ce3ea6a]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [40b202e9-887b-4fb2-ab63-6025a7cb100c, 94c6a26c-59ca-4e9e-9a17-0a707ded7c42, af054da0-2c6b-4f12-a0ee-b7e7f3c9e0f2, fa60d657-62f3-4de1-aa36-38ab94119bbf]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : c5c65207-d417-4638-8776-250c9ce3ea6a
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="672", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : af054da0-2c6b-4f12-a0ee-b7e7f3c9e0f2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bfb77e5d-fe5f-4b2e-8d7f-f1cfef8cb90f]
name                : "eth21"

_uuid               : 94c6a26c-59ca-4e9e-9a17-0a707ded7c42
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [07f6c0d3-39fd-4967-8851-767b816afe74]
name                : "eth22"

_uuid               : 40b202e9-887b-4fb2-ab63-6025a7cb100c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c36123a1-bb3a-4229-ac70-e8038bf9e60f]
name                : "br0"

_uuid               : fa60d657-62f3-4de1-aa36-38ab94119bbf
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4d68cf45-0e17-4659-8a54-99d268aa1f66]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4d68cf45-0e17-4659-8a54-99d268aa1f66
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9539004000, tx_dropped=0, tx_errors=0, tx_packets=6359336}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c36123a1-bb3a-4229-ac70-e8038bf9e60f
admin_state         : down
duplex              : full
ifindex             : 814
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

_uuid               : bfb77e5d-fe5f-4b2e-8d7f-f1cfef8cb90f
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
statistics          : {collisions=0, rx_bytes=46491524763, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31067089, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 07f6c0d3-39fd-4967-8851-767b816afe74
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31120228469, tx_dropped=0, tx_errors=0, tx_packets=20780259}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit c6bd5e91520990ac2a227cafd98857fa672949ed
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Tue Feb 16 11:13:35 2016 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Fri Feb 19 16:46:19 2016 -0800

    tests: Better tolerate file system restriction on file name length.
    
    ecryptfs on Linux restricts file names to 143 bytes, but these two tests
    used a 150-byte name.  This commit fixes the specific problem on ecryptfs
    by reducing the name it test to 143 bytes.  It also fixes the more general
    problem of name length restrictions by skipping the test, rather than
    failing it, if a directory with the 143-byte name cannot be created, since
    the most likely problem is that the name is too long for the file system.
    
    Reported-by: Zoltán Balogh &lt;zoltan.balogh@ericsson.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
</pre>
