---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b77d51ec-db40-4234-90c7-eb28d274e669
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port eth22
            Interface eth22
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 91027f91-d7f9-434b-b110-d82e7a84c0c6
controller          : [3db1b7fa-8c0d-4e22-b1da-1707e1f1fe33]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [4d42790b-3ab6-4fba-a45c-6b0bed6ed540, 57c07d1a-63f9-4a8a-8a0a-843bcd792a76, d3da65d0-a053-4095-89af-51e5418dd562, fbbb991f-00be-442b-b8dd-4e9e6fef9421]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3db1b7fa-8c0d-4e22-b1da-1707e1f1fe33
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=562, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : d3da65d0-a053-4095-89af-51e5418dd562
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [2dce395b-180c-4fdb-81e3-a2c46eb73076]
name                : br0

_uuid               : 57c07d1a-63f9-4a8a-8a0a-843bcd792a76
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [430873dd-1759-492a-91ab-96f99929aff1]
name                : eth22

_uuid               : fbbb991f-00be-442b-b8dd-4e9e6fef9421
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c012ed7e-3f45-4ac9-b9da-f2911edb9278]
name                : eth23

_uuid               : 4d42790b-3ab6-4fba-a45c-6b0bed6ed540
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e1118ea0-5117-431e-b7ab-5cf67bb76df4]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : e1118ea0-5117-431e-b7ab-5cf67bb76df4
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=3497120584, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2349296, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 430873dd-1759-492a-91ab-96f99929aff1
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1500
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1985315086, tx_dropped=0, tx_errors=0, tx_packets=1330722}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c012ed7e-3f45-4ac9-b9da-f2911edb9278
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1500
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1901319000, tx_dropped=0, tx_errors=0, tx_packets=1267546}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 2dce395b-180c-4fdb-81e3-a2c46eb73076
admin_state         : down
duplex              : full
ifindex             : 1153
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
commit bbbca389c002f740dffd0d8c24f13e562efaa876
Author:     Padmanabhan Krishnan &lt;kprad1@yahoo.com&gt;
AuthorDate: Thu Apr 24 13:18:18 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Apr 24 13:18:23 2014 -0700

    ofproto-dpif-xlate: Identify STP BPDUs more specifically.
    
    Apart from STP, EVB extension of LLDP as well as IEEE 802.1QBG use the
    Nearest Customer Bridge &#40;NCB&#41; DMAC which has a value of 0180.c200.0000.
    STP can be distinguished by Ethertype from these protocols.
    
    Signed-off-by: Padmanabhan Krishnan &lt;kprad1@yahoo.com&gt;
    [blp@nicira.com rewrote the details of the patch]
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Tested-by: Padmanabhan Krishnan &lt;kprad1@yahoo.com&gt;
</pre>
