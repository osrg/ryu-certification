---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
fe62b10e-7a29-4d73-812f-f9fd5e01b898
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth21"
            Interface "eth21"
        Port "eth23"
            Interface "eth23"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth22"
            Interface "eth22"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : ded04b9d-041f-42df-b86d-8f32b4caecd0
controller          : [42436f13-e511-4c3a-96cd-cdcb13988941]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [00aae4ba-f878-4175-8b9f-ff81d717db36, 105be012-122d-41d7-94b4-c68f295c6dda, 38742199-8d90-4e5a-aee7-f5ca04946bdc, 8c456342-3198-47dc-bbf6-48dff7b79d96]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 42436f13-e511-4c3a-96cd-cdcb13988941
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="646", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 38742199-8d90-4e5a-aee7-f5ca04946bdc
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bbd1db98-a324-44f1-b095-dca1f732bc56]
name                : "br0"

_uuid               : 8c456342-3198-47dc-bbf6-48dff7b79d96
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [69c9a6ad-8ffb-4e47-8163-62917579f944]
name                : "eth22"

_uuid               : 105be012-122d-41d7-94b4-c68f295c6dda
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0a6a8e57-1e4e-449c-ae6f-d4fc4684d5b2]
name                : "eth23"

_uuid               : 00aae4ba-f878-4175-8b9f-ff81d717db36
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [c6d99706-c028-4e6c-a208-1f487e57dc93]
name                : "eth21"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : bbd1db98-a324-44f1-b095-dca1f732bc56
admin_state         : down
duplex              : full
ifindex             : 953
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

_uuid               : 69c9a6ad-8ffb-4e47-8163-62917579f944
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631678609331, tx_dropped=0, tx_errors=0, tx_packets=421291738}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : c6d99706-c028-4e6c-a208-1f487e57dc93
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
statistics          : {collisions=0, rx_bytes=1234998938761, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=823723566, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 0a6a8e57-1e4e-449c-ae6f-d4fc4684d5b2
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=43475482500, tx_dropped=0, tx_errors=0, tx_packets=28983655}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d3de1af728326646d1a9fe686c6230b79e6d64c1
Author:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
AuthorDate: Mon Apr 27 14:48:46 2015 +0900
Commit:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
CommitDate: Tue Apr 28 10:03:16 2015 +0900

    datapath: Fix check-export-symbol for non-bash shells
    
    Avoid using a bash construct &#40;=~&#41; in the target.
    
    An alternative would be to make the configure script require
    bash explicitly.  &#40;Currently it doesn't and on NetBSD /bin/ksh
    is likely used.&#41;
    
    The code in question was introduced by
    commit b296b82a87326e68773b970284b8e012def0e3ba .
    &#40;&quot;datapath: Check the export of public functions in linux/compat/linux/.&quot;&#41;
    
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
    Acked-by: Alex Wang &lt;alexw@nicira.com&gt;
</pre>
