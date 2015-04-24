---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
d247c285-7449-4ddc-be7f-5b3f804ee768
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : a748a6b2-18a3-4a03-a99b-0a8ebcf9bfde
controller          : [37cab0bc-dae5-45fd-95cd-b3067793b449]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [0e881f24-03c0-4240-8861-73e4e7fd5df1, 4d1bc6ac-fdf0-4b6f-8825-3f6da7cebd4b, 6c76b06f-7008-4996-89e9-627c35183ed7, c58349bd-8674-4a72-9029-6626cc71ff16]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 37cab0bc-dae5-45fd-95cd-b3067793b449
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="662", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 0e881f24-03c0-4240-8861-73e4e7fd5df1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [720ee591-06b9-45be-b1c8-dbf27403f255]
name                : "eth22"

_uuid               : 4d1bc6ac-fdf0-4b6f-8825-3f6da7cebd4b
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [249d9fb1-d304-4a3d-b52b-6e9370c10186]
name                : "br0"

_uuid               : c58349bd-8674-4a72-9029-6626cc71ff16
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [9a0f96a9-670f-48d3-9f2f-83aa9e169378]
name                : "eth21"

_uuid               : 6c76b06f-7008-4996-89e9-627c35183ed7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [82041722-1a1e-43fc-bc00-791ce2e1613b]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 9a0f96a9-670f-48d3-9f2f-83aa9e169378
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
statistics          : {collisions=0, rx_bytes=1234180630486, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=823173530, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 720ee591-06b9-45be-b1c8-dbf27403f255
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=631310564892, tx_dropped=0, tx_errors=0, tx_packets=421044246}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 249d9fb1-d304-4a3d-b52b-6e9370c10186
admin_state         : down
duplex              : full
ifindex             : 939
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

_uuid               : 82041722-1a1e-43fc-bc00-791ce2e1613b
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=42861666000, tx_dropped=0, tx_errors=0, tx_packets=28574444}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 3ed424e5e5d614e08a58ffe700bbe88ed0514a7b
Author:     Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
AuthorDate: Thu Apr 23 20:27:53 2015 +0000
Commit:     Gurucharan Shetty &lt;gshetty@nicira.com&gt;
CommitDate: Thu Apr 23 14:49:33 2015 -0700

    datapath-windows: Removed gOvsCtrlLock global spinlock
    
    There is no need to use gOvsCtrlLock spinlock to guard the switch
    context, as there is now the switch context's reference count used
    for this purpose.
    
    Now the gOvsCtrlLock spinlock guards only one shared resource, the
    OVS_OPEN_INSTANCE global instance array.
    
    Signed-off-by: Sorin Vinturis &lt;svinturis@cloudbasesolutions.com&gt;
    Acked-by: Nithin Raju &lt;nithin@vmware.com&gt;
    Signed-off-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
