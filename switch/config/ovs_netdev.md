---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
df7f8ee1-4fe7-48b2-ad89-b3c667cc7284
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
_uuid               : 9ebad573-51be-47cb-8297-573023103782
controller          : [67d9f686-1ce3-4fdd-a8d8-780dfb022da1]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [46287570-4e28-4502-b1e5-dd8b0c18c6a5, 70e3b3c7-72e3-431c-872b-98a9180fe487, 8f7ce43b-deab-47f4-a903-059cdee236b2, ae0e4878-587f-4744-bd94-fd355b7c522d]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 67d9f686-1ce3-4fdd-a8d8-780dfb022da1
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="657", sec_since_disconnect="1", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 46287570-4e28-4502-b1e5-dd8b0c18c6a5
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b2ebfb67-4c10-4249-b341-6ee18dd9fbaf]
name                : "eth21"

_uuid               : ae0e4878-587f-4744-bd94-fd355b7c522d
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [5fefcf6b-4e33-4f7a-a190-dfa66d850fa3]
name                : "eth22"

_uuid               : 70e3b3c7-72e3-431c-872b-98a9180fe487
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [fb355fda-5c93-4fcc-9146-56165abf73a5]
name                : "eth23"

_uuid               : 8f7ce43b-deab-47f4-a903-059cdee236b2
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ddbb9a14-53e9-4511-bebe-102976c49b9b]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : ddbb9a14-53e9-4511-bebe-102976c49b9b
admin_state         : down
duplex              : full
ifindex             : 819
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

_uuid               : fb355fda-5c93-4fcc-9146-56165abf73a5
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=37598547000, tx_dropped=0, tx_errors=0, tx_packets=25065698}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 5fefcf6b-4e33-4f7a-a190-dfa66d850fa3
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=602545955821, tx_dropped=0, tx_errors=0, tx_packets=401847996}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : b2ebfb67-4c10-4249-b341-6ee18dd9fbaf
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
statistics          : {collisions=0, rx_bytes=1192832547457, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=795566346, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 4e5e44e30133939b792a013a812c84f564ffa8aa
Author:     Alex Wang &lt;alexw@nicira.com&gt;
AuthorDate: Fri Mar 27 23:19:22 2015 -0700
Commit:     Alex Wang &lt;alexw@nicira.com&gt;
CommitDate: Sat Mar 28 14:31:47 2015 -0700

    ofproto-dpif: Set need_revalidate when removing cfm from ofport.
    
    When cfm is deleted from a port, all modules should release their
    reference so that the cfm struct can be removed from the global hmap
    and freed.  Therein, the reference held by xlate module can only be
    released when the need_revalidate flag is set &#40;e.g set to
    REV_RECONFIGURE&#41;.  And this flag should be set while removing cfm
    from ofport.  Unfortunately, this has never been done before and the
    bug was hidden by another bug fixed in recent commit a190839
    &#40;netdev-vport: Do not update netdev when there is no config change.&#41;
    
    To fix this issue, this commit makes the code set need_revalidate
    when removing cfm from ofport.
    
    Signed-off-by: Alex Wang &lt;alexw@nicira.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
