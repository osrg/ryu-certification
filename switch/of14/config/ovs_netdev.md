---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c8b88eba-4cd5-40d0-8b3f-2217de5eede2
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1e5231fb-a67e-440c-8490-f72f2a2b6f6b
controller          : [b20441d0-7749-40e0-b9cc-107cc792b762]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0a4aee1f-414d-46ee-8a03-b14a7d0e95a4, 232cf4e5-8cf0-4a60-ac5d-56efaa28f9a5, 6e7e5d97-e860-49fa-b504-27ce534dad76, 76a62ce1-a207-4500-b777-453385255b5e]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b20441d0-7749-40e0-b9cc-107cc792b762
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="16", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 232cf4e5-8cf0-4a60-ac5d-56efaa28f9a5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [600c08f6-afa6-4988-bb97-5836e258d675]
name                : "eth22"

_uuid               : 76a62ce1-a207-4500-b777-453385255b5e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [95dee11d-5e3e-4760-af4b-6679b692f0ff]
name                : "br0"

_uuid               : 6e7e5d97-e860-49fa-b504-27ce534dad76
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [67be2081-afc2-4b5d-87b6-1a0c62ccc52a]
name                : "eth23"

_uuid               : 0a4aee1f-414d-46ee-8a03-b14a7d0e95a4
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [38516598-e653-4ead-bdfa-ef9bc42c344b]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 38516598-e653-4ead-bdfa-ef9bc42c344b
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
statistics          : {collisions=0, rx_bytes=42981030807, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=28707036, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 67be2081-afc2-4b5d-87b6-1a0c62ccc52a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=6907437000, tx_dropped=0, tx_errors=0, tx_packets=4604958}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 95dee11d-5e3e-4760-af4b-6679b692f0ff
admin_state         : down
duplex              : full
ifindex             : 700
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

_uuid               : 600c08f6-afa6-4988-bb97-5836e258d675
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=29540552753, tx_dropped=0, tx_errors=0, tx_packets=19717528}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 482553cca80f018d705b93b846182067fd272cdd
Author:     Ben Pfaff &lt;blp@ovn.org&gt;
AuthorDate: Wed Dec 16 23:32:54 2015 -0800
Commit:     Ben Pfaff &lt;blp@ovn.org&gt;
CommitDate: Fri Dec 18 21:58:57 2015 -0800

    tun-metadata: Fix memory leak in tun_metadata_add_entry&#40;&#41; corner case.
    
    Found by valgrind.
    
    Reported-by: William Tu &lt;u9012063@gmail.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@ovn.org&gt;
    Acked-by: Jesse Gross &lt;jesse@kernel.org&gt;
</pre>
