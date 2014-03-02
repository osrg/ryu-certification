---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
c16898a8-3110-48f4-8e9f-92dd9dd5c05c
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth7
            Interface eth7
        Port eth8
            Interface eth8
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 125cc18b-3153-4e39-824b-9b8726e9c3b4
controller          : [b7b50b24-add8-481a-b7c9-6cad57c9dcd9]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [887ea29d-ca09-4643-bcee-21010243cd01, 99ca84a4-6c2f-49fb-b5fa-111020d5c3a7, c62d6ff1-84b0-499c-b020-e8a629aad56b]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : b7b50b24-add8-481a-b7c9-6cad57c9dcd9
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=1, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 99ca84a4-6c2f-49fb-b5fa-111020d5c3a7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c95b57a7-b8bb-4836-a9ed-032dbedd3a68]
name                : eth8

_uuid               : c62d6ff1-84b0-499c-b020-e8a629aad56b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5b8fdd4c-6052-4fbc-af93-a8cbeaac08a6]
name                : br0

_uuid               : 887ea29d-ca09-4643-bcee-21010243cd01
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [f5cca7be-80cd-4bc7-bd85-be8c89e12d21]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 5b8fdd4c-6052-4fbc-af93-a8cbeaac08a6
admin_state         : up
duplex              : full
ifindex             : 417
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 2
link_speed          : 10000000
link_state          : up
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : f5cca7be-80cd-4bc7-bd85-be8c89e12d21
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
statistics          : {collisions=0, rx_bytes=3061059490, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72612893, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : c95b57a7-b8bb-4836-a9ed-032dbedd3a68
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3062304, tx_dropped=0, tx_errors=0, tx_packets=32682}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 87972a8fcd0f339c7229a014edd4c75fd9c1356c
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Sat Mar 1 17:15:00 2014 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Sat Mar 1 17:38:09 2014 -0800

    tunnel: Do not set padding bits in tunnel mask.
    
    On most architectures other than 32-bit x86, struct flow_tnl ends with 4
    padding bytes.  Until now, tnl_xlate_init() set those bytes to nonzero
    values in the wildcard mask.  When the wildcard mask passed through Netlink
    attributes and back to userspace, the padding bytes of course became zero
    again, which caused a wildcard mask mismatch and premature deletion of the
    flow in revalidation.  This commit fixes the problem.
    
    Bug #1192516.
    Reported-by: Krishna Miriyala &lt;miriyalak@vmware.com&gt;
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Ethan Jackson &lt;ethan@nicira.com&gt;
</pre>
