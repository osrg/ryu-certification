---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
50eb541d-ac41-4744-aaab-1cdbb5801a0b
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
_uuid               : 13882cd0-8c2a-4e3b-830e-0cc4efac42e7
controller          : [fb7f22f1-0ccd-4111-b752-2187eb4b1a9c]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [17582fd8-7987-4964-8277-e903637a06df, 6dcc9158-1974-48ef-9ca2-9f3db55fd9b7, ddbb7b31-cdad-4a27-9412-d05f52f4bff2]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : fb7f22f1-0ccd-4111-b752-2187eb4b1a9c
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=377, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6dcc9158-1974-48ef-9ca2-9f3db55fd9b7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dfcb20ba-89ec-48b3-8089-ac4dfe0d1f71]
name                : eth8

_uuid               : 17582fd8-7987-4964-8277-e903637a06df
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [329a1a6a-ec4b-4e64-8be3-67d4e4aad4a1]
name                : eth7

_uuid               : ddbb7b31-cdad-4a27-9412-d05f52f4bff2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [66bcb310-7db6-4915-9642-2bcf204a3a68]
name                : br0

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 66bcb310-7db6-4915-9642-2bcf204a3a68
admin_state         : up
duplex              : full
ifindex             : 662
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

_uuid               : 329a1a6a-ec4b-4e64-8be3-67d4e4aad4a1
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
statistics          : {collisions=0, rx_bytes=3067324906, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72676457, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : dfcb20ba-89ec-48b3-8089-ac4dfe0d1f71
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=4906210, tx_dropped=0, tx_errors=0, tx_packets=52314}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3e634810dac461f2e0dbfef0d0134ed5471c7a38
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Tue Dec 31 10:35:27 2013 -0800
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu Mar 20 14:06:27 2014 -0700

    odp-util: Fix VLAN parsing behavior in parse_8021q_onward().
    
    Anytime there is a VLAN the flow needs to properly reflect that.  Keeping
    the TPID in dl_type never makes sense and will probably cause problems.
    The existing code did the right thing in the common case but not in corner
    cases where it returned ODP_FIT_TOO_MUCH or ODP_FIT_TOO_LITTLE (the cases
    where it returned an error don't matter since nothing looks at the flow
    in that case).
    
    Found by inspection.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
