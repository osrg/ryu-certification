---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
6e4d0a15-586c-479f-8255-112da9493ff6
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : b8314132-dcd4-4f30-bf6e-5c333ce2d4d8
controller          : [60f17d35-897b-44bd-8421-82e841dcf8a9]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [43ac8d9b-1ba6-48d5-8483-0c6ed974c714, 5611c9a6-679a-4201-ae9e-3608a0dcc9f3, 6ddd1958-9cba-4a75-a633-335ecee53569, e8a7dcf6-031b-4e2a-b8bc-93fd402ac5ce]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 60f17d35-897b-44bd-8421-82e841dcf8a9
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=552, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 6ddd1958-9cba-4a75-a633-335ecee53569
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [abbd98ae-d3a2-44cf-8f17-4f7eca227b9e]
name                : eth23

_uuid               : e8a7dcf6-031b-4e2a-b8bc-93fd402ac5ce
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [bd4906c6-ed35-4947-84be-78a5a00404da]
name                : eth22

_uuid               : 5611c9a6-679a-4201-ae9e-3608a0dcc9f3
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [7f2633b2-a75f-488b-aea1-9ff09432c25c]
name                : br0

_uuid               : 43ac8d9b-1ba6-48d5-8483-0c6ed974c714
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [a8a3034c-488c-463d-8d1b-99690055cb85]
name                : eth21

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : a8a3034c-488c-463d-8d1b-99690055cb85
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
statistics          : {collisions=0, rx_bytes=4263470287, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=2860033, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : abbd98ae-d3a2-44cf-8f17-4f7eca227b9e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=2986470000, tx_dropped=0, tx_errors=0, tx_packets=1990980}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 7f2633b2-a75f-488b-aea1-9ff09432c25c
admin_state         : down
duplex              : full
ifindex             : 208
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

_uuid               : bd4906c6-ed35-4947-84be-78a5a00404da
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1689491236, tx_dropped=0, tx_errors=0, tx_packets=1132847}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit a6ce4b9d2518a261f0d8f51acef069d687b8df2e
Author:     Ben Pfaff &lt;blp@nicira.com&gt;
AuthorDate: Thu May 15 15:52:17 2014 -0700
Commit:     Ben Pfaff &lt;blp@nicira.com&gt;
CommitDate: Thu May 15 15:53:47 2014 -0700

    ofproto-dpif-upcall: Avoid use-after-free in revalidate&#40;&#41; corner cases.
    
    The loop in revalidate&#40;&#41; needs to ensure that any data obtained from
    dpif_flow_dump_next&#40;&#41; is used before it is destroyed, as indicated by
    dpif_flow_dump_next_may_destroy_keys&#40;&#41;.  In the common case, where
    processing reaches the end of the main &quot;while&quot; loop, it does this, but
    in two corner cases the code in the loop execute &quot;continue;&quot;, which skipped
    the check.  This commit fixes the problem.
    
    Bug #1249988.
    Signed-off-by: Ben Pfaff &lt;blp@nicira.com&gt;
    Acked-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
