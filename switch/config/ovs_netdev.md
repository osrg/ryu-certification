---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
3a2f4b05-49cd-4894-8ab9-856c74cb3b4d
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
_uuid               : 36f9b230-f6e4-4fd2-8e1e-24503b3979f8
controller          : [5010bd19-4523-492c-b341-6ad9ad93fd60]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [059cc26f-5382-4779-b8f9-09f36c27fa96, ceb72112-ddb5-4c41-a7de-5f7566b5bf61, e013264d-ddb4-4051-b3ad-7cf69b8c6d99]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 5010bd19-4523-492c-b341-6ad9ad93fd60
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : e013264d-ddb4-4051-b3ad-7cf69b8c6d99
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [4ce98310-efd7-419e-b877-ab9fc36309ad]
name                : br0

_uuid               : ceb72112-ddb5-4c41-a7de-5f7566b5bf61
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [cadb7cef-993e-4d5f-9864-06674a255f76]
name                : eth8

_uuid               : 059cc26f-5382-4779-b8f9-09f36c27fa96
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [d807521f-35c4-465a-a56b-688ee8cec5c2]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 4ce98310-efd7-419e-b877-ab9fc36309ad
admin_state         : up
duplex              : full
ifindex             : 543
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

_uuid               : d807521f-35c4-465a-a56b-688ee8cec5c2
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
statistics          : {collisions=0, rx_bytes=3064464708, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72647443, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : cadb7cef-993e-4d5f-9864-06674a255f76
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4063838, tx_dropped=0, tx_errors=0, tx_packets=43346}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 1b5b50718fc608d42c4ba985f23fab10816d1853
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Thu Mar 13 21:48:55 2014 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Sat Mar 15 21:18:32 2014 -0700

    udpif:  Bug fix updif_flush
    
    Before this commit, all datapath flows are cleared with dpif_flush(),
    but the revalidator thread still holds ukeys, which are caches of the
    datapath flows in the revalidaor.  Flushing ukeys causes flow_del
    messages to be sent to the datapath again on flows that have been
    deleted by the dpif_flush() already.
    
    Double deletion by itself is not problem, per se, may an efficiency
    issue. However, for ever flow_del message sent to the datapath, a log
    message, at the warning level, will be generated in case datapath
    failed to execute the command. In addition to cause spurious log
    messages, Double deletion causes unit tests to report erroneous
    failures as all warning messages are considered test failures.
    
    The fix is to simply shut down the revalidator threads to flush all
    ukeys, then flush the datapth before restarting the revalidator threads.
    
    dpif_flush() was implemented as flush flows of all datapaths while
    most of its invocation should only flush its local datapath.
    Only megaflow on/off commands should flush all dapapaths. This bug is
    also fixed.
    
    Found during development.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Jarno Rajahalme &lt;jrajahalme@nicira.com&gt;
</pre>
