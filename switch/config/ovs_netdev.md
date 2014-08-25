---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
936ac19d-b504-417d-b34e-5ef973285913
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
_uuid               : f0afc822-152b-4355-ad1e-ad3b6e6eaef5
controller          : [73945519-3bab-4fe9-867f-fabadc195ea7]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
mcast_snooping_enable: false
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [6a88290d-683e-48e7-8034-671711fb09de, 8e56cad8-76b7-4c75-aaff-5f45b986a572, 96d5c957-f276-4fe5-aec4-f9d14c3dddff, f76be81f-198c-4844-9c69-06340ff74f5c]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 73945519-3bab-4fe9-867f-fabadc195ea7
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=662, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8e56cad8-76b7-4c75-aaff-5f45b986a572
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ceabcb50-c987-40a6-8076-83a21481d9de]
name                : eth22

_uuid               : 6a88290d-683e-48e7-8034-671711fb09de
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [97774d5c-7c9a-43ce-aafd-0c5fd7340603]
name                : eth21

_uuid               : 96d5c957-f276-4fe5-aec4-f9d14c3dddff
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [20b87611-102b-400a-b62b-4b24de40b0bb]
name                : br0

_uuid               : f76be81f-198c-4844-9c69-06340ff74f5c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [acb89520-91bc-401f-a6f1-fb48cfdf7e3d]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 97774d5c-7c9a-43ce-aafd-0c5fd7340603
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=1451873333, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=9569063, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : ceabcb50-c987-40a6-8076-83a21481d9de
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1288789740, tx_dropped=0, tx_errors=0, tx_packets=6590966}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : acb89520-91bc-401f-a6f1-fb48cfdf7e3d
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1618720500, tx_dropped=0, tx_errors=0, tx_packets=1079147}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 20b87611-102b-400a-b62b-4b24de40b0bb
admin_state         : down
duplex              : full
ifindex             : 57
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
commit 0725e74731e4ea3e49dae7200835050f0b726c88
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Fri Aug 22 15:32:19 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Mon Aug 25 08:54:01 2014 -0700

    ofproto-dpif-xlate: Drop 'may_learn' parameter from xlate_push_stats&#40;&#41;.
    
    Both existing callers calculated 'may_learn' as 'stats-&gt;n_packets &gt; 0', so
    it was redundant.  Because xlate_push_stats&#40;&#41; is now entirely a no-op if
    'stats-&gt;n_packets' is 0, we can now delete the tests entirely from the
    cases that previously only ran if 'may_learn'.
    
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
