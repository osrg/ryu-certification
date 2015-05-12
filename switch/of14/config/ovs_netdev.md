---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
03081209-cb48-447a-9efe-02984681224a
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
_uuid               : 9d64b20b-6238-4f2d-875e-76a0e4f87f3d
controller          : [08a4950e-f1c1-403f-adeb-ea412f67dae7]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [3b83a84a-ec39-4ded-bb2b-acf50514118e, b730cb38-6695-4218-8523-14d3eccf3f17, c659252b-4805-4110-ae7d-32ad824dff82, d3813265-5e02-4b0d-9f1c-e5cfcba6dae2]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 08a4950e-f1c1-403f-adeb-ea412f67dae7
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="646", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : b730cb38-6695-4218-8523-14d3eccf3f17
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a3e25fdc-5778-468c-967a-56ddf9ce2c28]
name                : "eth21"

_uuid               : d3813265-5e02-4b0d-9f1c-e5cfcba6dae2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9fd090c7-814a-4f78-8efc-2ab1ec76cc14]
name                : "eth22"

_uuid               : 3b83a84a-ec39-4ded-bb2b-acf50514118e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b62eaae8-a5bf-49e7-9a5f-fdc5c5867194]
name                : "br0"

_uuid               : c659252b-4805-4110-ae7d-32ad824dff82
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [260a9363-7a3d-48e6-9027-e5195fb17ff1]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a3e25fdc-5778-468c-967a-56ddf9ce2c28
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
statistics          : {collisions=0, rx_bytes=12279588746, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=8192935, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b62eaae8-a5bf-49e7-9a5f-fdc5c5867194
admin_state         : down
duplex              : full
ifindex             : 43
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

_uuid               : 260a9363-7a3d-48e6-9027-e5195fb17ff1
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=748425000, tx_dropped=0, tx_errors=0, tx_packets=498950}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 9fd090c7-814a-4f78-8efc-2ab1ec76cc14
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=9885572532, tx_dropped=0, tx_errors=0, tx_packets=6593267}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 9899125aaae9f0634f43307cc0ff72f5afb287bb
Author:     Oleg Strikov &lt;oleg.strikov@canonical.com&gt;
AuthorDate: Fri May 8 12:05:13 2015 -0700
Commit:     Pravin B Shelar &lt;pshelar@nicira.com&gt;
CommitDate: Tue May 12 09:14:12 2015 -0700

    INSTALL.DPDK: Notes on running ovs-vswitchd/dpdk inside a VM
    
    Additional configuration is required if you want to run ovs-vswitchd
    with DPDK backend inside a QEMU virtual machine. This happens because,
    by default, virtio NIC provided to the guest doesn't support multiple
    TX queues which are required by ovs-vswitchd/dpdk. This commit updates
    INSTALL.DPDK.md to provide guidelines on how to enable support for
    multiple TX queues using QEMU command line and Libvirt config file.
    
    Signed-off-by: Oleg Strikov &lt;oleg.strikov@canonical.com&gt;
    Acked-by: Pravin B Shelar &lt;pshelar@nicira.com&gt;
</pre>
