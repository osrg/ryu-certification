---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b67e0100-54ab-409b-9b0a-d230b0cc9c5e
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 3cb45d25-bbf5-4cc0-bfaa-96db77e63d3c
controller          : [88d60c3a-513b-4dad-a276-80734b845a4c]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [48b8d6cd-2ee2-4b47-89e2-16ec89cac3a7, 79d092d9-bb6c-491d-a5df-a7aecc5decae, b952d277-9b86-4cde-aee0-32a7d0aa191f, c4e749d8-69b5-4f8e-8058-699c0773364f]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 88d60c3a-513b-4dad-a276-80734b845a4c
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="17", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : c4e749d8-69b5-4f8e-8058-699c0773364f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [06c76b76-6f83-49e0-9504-28482891af29]
name                : "br0"

_uuid               : 79d092d9-bb6c-491d-a5df-a7aecc5decae
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6a198c6d-0d52-488e-bd21-afbce421d120]
name                : "eth21"

_uuid               : 48b8d6cd-2ee2-4b47-89e2-16ec89cac3a7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bbf69b01-2021-4fef-90a8-655c99f21e3a]
name                : "eth22"

_uuid               : b952d277-9b86-4cde-aee0-32a7d0aa191f
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [740f3117-980d-43f2-acfb-1ec6f6737b48]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 6a198c6d-0d52-488e-bd21-afbce421d120
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
statistics          : {collisions=0, rx_bytes=46491525021, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=31067092, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : bbf69b01-2021-4fef-90a8-655c99f21e3a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=31120228727, tx_dropped=0, tx_errors=0, tx_packets=20780262}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 06c76b76-6f83-49e0-9504-28482891af29
admin_state         : down
duplex              : full
ifindex             : 816
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

_uuid               : 740f3117-980d-43f2-acfb-1ec6f6737b48
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
