---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
2b7da493-9d1d-4335-b0eb-bba6d43587ea
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
_uuid               : ba875306-446f-453a-b4a5-6db20b74e905
controller          : [22c911a5-5127-4caf-96ce-658d53de9054]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [b6c5d183-0eda-43ae-8bfe-2eabe4ce5114, c242f259-a7bb-4787-be01-3300f9760ec3, e532c284-eedd-415c-852b-c85efde7abdd]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 22c911a5-5127-4caf-96ce-658d53de9054
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=297, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e532c284-eedd-415c-852b-c85efde7abdd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [224a4930-47ca-4347-a662-f73405b74fda]
name                : eth7

_uuid               : c242f259-a7bb-4787-be01-3300f9760ec3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [864aa24c-ef46-4398-a64e-c4a5baf0d9be]
name                : eth8

_uuid               : b6c5d183-0eda-43ae-8bfe-2eabe4ce5114
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [22cf8b12-7ac6-41bb-89d9-f0e1636a158e]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 864aa24c-ef46-4398-a64e-c4a5baf0d9be
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=497966, tx_dropped=0, tx_errors=0, tx_packets=5320}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 224a4930-47ca-4347-a662-f73405b74fda
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
statistics          : {collisions=0, rx_bytes=3052994525, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72531355, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : 22cf8b12-7ac6-41bb-89d9-f0e1636a158e
admin_state         : up
duplex              : full
ifindex             : 91
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 0a8763fcb31bfca0d8d854c235c531005088fcb9
Author:     Ethan Jackson &lt;ethan@nicira.com&gt;
AuthorDate: Mon Jan 27 16:40:27 2014 -0800
Commit:     Ethan Jackson &lt;ethan@nicira.com&gt;
CommitDate: Wed Jan 29 12:31:32 2014 -0800

    ofproto-dpif-upcall: Hardcode max_idle to 1500ms.
    
    Before this patch, OVS tried to guess an optimal max idle time for
    datapath flows based on the number of datapath flows relative to the
    limit.  This caused instability because the limit was based on the
    dump duration which was affected by the max idle time.  This patch
    chooses instead to hardcode the max idle time to 1.5s except in
    extreme case where the datapath flow limit is exceeded.  1.5s was
    chosen to ensure pings occurring at once per second stay cached in the
    datapath.
    
    Signed-off-by: Ethan Jackson &lt;ethan@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
