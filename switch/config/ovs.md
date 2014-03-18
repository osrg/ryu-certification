---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
835b77b2-a912-40d4-81af-18145bd49205
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth8
            Interface eth8
        Port eth7
            Interface eth7

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 0324677e-04b9-4807-bbc9-102d784f4b11
controller          : [b2881855-9eba-40f4-8c36-dfdb69a9899b]
datapath_id         : 0000000000000001
datapath_type       : 
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [026323fa-559a-4d3e-aeb1-5e8ee54d1529, bdb2f4b9-5262-44de-8aa3-bc8f50096701, d5793171-251f-440d-ab6f-51502168b3ed]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b2881855-9eba-40f4-8c36-dfdb69a9899b
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : bdb2f4b9-5262-44de-8aa3-bc8f50096701
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3387a3f0-9419-425f-8436-d9e2dd2aff3a]
name                : eth8

_uuid               : d5793171-251f-440d-ab6f-51502168b3ed
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3d2519b4-940b-4456-8e1a-70508dd6033e]
name                : eth7

_uuid               : 026323fa-559a-4d3e-aeb1-5e8ee54d1529
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7b5f25d3-39d0-4c9e-82b5-33a0753b9821]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3387a3f0-9419-425f-8436-d9e2dd2aff3a
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 3d2519b4-940b-4456-8e1a-70508dd6033e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 7b5f25d3-39d0-4c9e-82b5-33a0753b9821
admin_state         : up
ifindex             : 584
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1550
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=openvswitch}
type                : internal
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 26e1fdc46c820354fe1345cb0c56b6fb77b04492
Author:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
AuthorDate: Mon Mar 17 09:28:07 2014 -0700
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Tue Mar 18 13:18:58 2014 -0700

    stream: Call WSAStartup() before calling any winsock functions.
    
    The WSAStartup function initiates use of the Winsock DLL by a process.
    The function should be called before any winsock related functions
    are called.
    
    Since, we use stream-fd-windows through pstream_open or stream_open
    add the WSAStartup() call there.
    
    The current version of the Windows Sockets specification is version 2.2
    
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
