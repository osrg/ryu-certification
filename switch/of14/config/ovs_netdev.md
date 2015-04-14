---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
612c5cf4-bf3c-4b7b-8c72-8f1322bd4060
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "eth23"
            Interface "eth23"
        Port "eth21"
            Interface "eth21"
        Port "eth22"
            Interface "eth22"
        Port "br0"
            Interface "br0"
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 1e89a4bd-ae11-43d7-a8d7-c95b9fa07faf
controller          : [3c3da81d-1eaa-47d2-b6c4-3e192d2e781b]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [53691b0d-dff4-404a-8eaf-aa56b2898bc7, 6086649e-6928-42bd-89d9-e704ed161655, 8bea4741-82ea-4aba-b34f-d39516c0e335, efc49b6b-a36f-4980-9d28-142e50e3c4da]
protocols           : ["OpenFlow14"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 3c3da81d-1eaa-47d2-b6c4-3e192d2e781b
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_connect="647", sec_since_disconnect="2", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 8bea4741-82ea-4aba-b34f-d39516c0e335
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bbfa6e46-b875-4334-b17a-f3061d3ecd69]
name                : "eth22"

_uuid               : 53691b0d-dff4-404a-8eaf-aa56b2898bc7
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ca648e53-b9ec-440a-9932-86cc32c86822]
name                : "eth23"

_uuid               : 6086649e-6928-42bd-89d9-e704ed161655
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [99ccc59c-0f6c-4386-94e7-2e8e1ec60730]
name                : "eth21"

_uuid               : efc49b6b-a36f-4980-9d28-142e50e3c4da
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [da125f15-279f-45ec-8653-e7d3bb7acc88]
name                : "br0"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 99ccc59c-0f6c-4386-94e7-2e8e1ec60730
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
statistics          : {collisions=0, rx_bytes=1231491620011, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=821366080, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : da125f15-279f-45ec-8653-e7d3bb7acc88
admin_state         : down
duplex              : full
ifindex             : 893
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

_uuid               : bbfa6e46-b875-4334-b17a-f3061d3ecd69
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=630101423021, tx_dropped=0, tx_errors=0, tx_packets=420231156}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : ca648e53-b9ec-440a-9932-86cc32c86822
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=40844391000, tx_dropped=0, tx_errors=0, tx_packets=27229594}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit d663136e85bdb88ec11c617bbf07570f612b81e4
Author:     Andy Zhou &lt;azhou@nicira.com&gt;
AuthorDate: Tue Apr 14 12:28:50 2015 -0700
Commit:     Andy Zhou &lt;azhou@nicira.com&gt;
CommitDate: Tue Apr 14 14:08:47 2015 -0700

    perf-counters: fix non-linux build
    
    Commit '97a3c43515e' misses definitions for non-Linux platforms thus
    broke builds for any non-Linux platform.
    
    Signed-off-by: Andy Zhou &lt;azhou@nicira.com&gt;
    Acked-by: Gurucharan Shetty &lt;gshetty@nicira.com&gt;
</pre>
