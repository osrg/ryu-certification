---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
b6c771c4-b788-443a-95e5-267f375ceced
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : de11d28f-12f3-49d1-b8ff-7adbd8bb6f09
controller          : [bc7a7eb5-033c-4627-a9d5-daaf82c968dc]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [27bd8217-9b1d-459d-b882-de37132ac006, 807fd6c3-d337-40f6-b8b4-ca104504f270, 9ea24f35-6b45-4da5-864e-8ae89a836843, c500e071-7139-41c2-b815-b440c40c96f1]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bc7a7eb5-033c-4627-a9d5-daaf82c968dc
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=977, sec_since_disconnect=3, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 9ea24f35-6b45-4da5-864e-8ae89a836843
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [317f01e9-6810-4eaa-adb5-f5d0dd8485b3]
name                : eth22

_uuid               : c500e071-7139-41c2-b815-b440c40c96f1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [6bda2eb5-0d06-43a4-8dfe-f3a5f27ff653]
name                : eth21

_uuid               : 27bd8217-9b1d-459d-b882-de37132ac006
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [abefce9b-b9ae-4f69-98a3-69587c9c5a69]
name                : br0

_uuid               : 807fd6c3-d337-40f6-b8b4-ca104504f270
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [e3689a93-7cb9-42a9-8f22-0170995f76e0]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 317f01e9-6810-4eaa-adb5-f5d0dd8485b3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=3329246282, tx_dropped=0, tx_errors=0, tx_packets=33759853}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 6bda2eb5-0d06-43a4-8dfe-f3a5f27ff653
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
statistics          : {collisions=0, rx_bytes=1476241768, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=81270330, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : e3689a93-7cb9-42a9-8f22-0170995f76e0
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
statistics          : {collisions=0, rx_bytes=58500, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=39, tx_bytes=2745428080, tx_dropped=0, tx_errors=0, tx_packets=10420904}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : abefce9b-b9ae-4f69-98a3-69587c9c5a69
admin_state         : down
duplex              : full
ifindex             : 607
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
