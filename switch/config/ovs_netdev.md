---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d7de33f6-8297-4b41-8c4a-b5186de30dc5
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth22
            Interface eth22
        Port eth23
            Interface eth23
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 7bd37807-168b-4301-87d4-2910bfeae890
controller          : [ee0ba033-6f99-48cc-a71c-ebb77d75a248]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [207bf80d-7d9b-46d2-bc0a-7019de8aecfd, 7128ec39-a129-42f3-9e4d-3d4149ee0447, 817d758f-9e1c-4766-a9bf-189723590a26, ab0d5b91-bc07-4267-a816-dc5e39398ffa]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : ee0ba033-6f99-48cc-a71c-ebb77d75a248
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=982, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : ab0d5b91-bc07-4267-a816-dc5e39398ffa
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c25baf0d-59aa-46c3-ad39-1ba6d674c036]
name                : br0

_uuid               : 7128ec39-a129-42f3-9e4d-3d4149ee0447
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0b1029f0-a8ec-40ab-916b-0b18cac668f4]
name                : eth23

_uuid               : 207bf80d-7d9b-46d2-bc0a-7019de8aecfd
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3937cb41-6c4d-4786-b835-0593f0b41c63]
name                : eth22

_uuid               : 817d758f-9e1c-4766-a9bf-189723590a26
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c0b5316c-9db5-4421-b37d-3999e6307464]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : c0b5316c-9db5-4421-b37d-3999e6307464
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
statistics          : {collisions=0, rx_bytes=1359350772, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=81191772, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0b1029f0-a8ec-40ab-916b-0b18cac668f4
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2646206080, tx_dropped=0, tx_errors=0, tx_packets=10354756}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 3937cb41-6c4d-4786-b835-0593f0b41c63
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3288220948, tx_dropped=0, tx_errors=0, tx_packets=33732271}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : c25baf0d-59aa-46c3-ad39-1ba6d674c036
admin_state         : down
duplex              : full
ifindex             : 605
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
commit df1a9a49387912670bc226851c35f666b9aa5383
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Mon Jun 23 15:52:03 2014 +0000
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Tue Jun 24 09:56:01 2014 +1200

    Revert &quot;revalidator: Use xcache when revalidation is required.&quot;
    
    This reverts commit a48c85b2d672505b89e488d28066538705b94942. The commit
    was causing intermittent testsuite failures and unexpected re-install of
    stale mac-learning entries.
    
    VMware-BZ: 1268574
    
    Reported-by: Len Gao &lt;leng@vmware.com&gt;
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
