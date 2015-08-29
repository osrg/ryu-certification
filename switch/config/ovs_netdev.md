---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
7e898507-7b9a-4ea8-8a8f-51159927f53b
    Bridge "br0"
        Controller "tcp:10.24.150.30:6633"
        fail_mode: secure
        Port "br0"
            Interface "br0"
                type: internal
        Port "eth23"
            Interface "eth23"
        Port "eth22"
            Interface "eth22"
        Port "eth21"
            Interface "eth21"

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : 08413c9e-9d86-4699-b7af-a5a850d712c8
controller          : [bb3ccbc7-02cd-40b4-bf4e-58db89c303c5]
datapath_id         : "0000000000000001"
datapath_type       : netdev
datapath_version    : "<built-in>"
fail_mode           : secure
mcast_snooping_enable: false
name                : "br0"
other_config        : {datapath-id="0000000000000001"}
ports               : [438266c9-d4cf-4ef5-9311-227f24ee76ef, 4b2e23f6-fbc1-4489-a7cc-fb3abbb5f9a9, 7a9fa164-e9ef-4161-9b0c-bd17b92a38e0, 885cb548-16cf-408b-a0cd-652034fd133c]
protocols           : ["OpenFlow13"]
rstp_enable         : false
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : bb3ccbc7-02cd-40b4-bf4e-58db89c303c5
is_connected        : false
role                : other
status              : {last_error="Connection refused", sec_since_disconnect="3", state=BACKOFF}
target              : "tcp:10.24.150.30:6633"

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : 7a9fa164-e9ef-4161-9b0c-bd17b92a38e0
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [51bac33d-e4ac-4656-9700-f9da12ce0c54]
name                : "eth22"

_uuid               : 885cb548-16cf-408b-a0cd-652034fd133c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [60cc5274-1a04-4ce2-91bb-ef669cb4baef]
name                : "eth21"

_uuid               : 438266c9-d4cf-4ef5-9311-227f24ee76ef
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3496c1f9-c608-4137-beb1-ce4338945cf4]
name                : "br0"

_uuid               : 4b2e23f6-fbc1-4489-a7cc-fb3abbb5f9a9
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [3c8dc910-24a1-455b-924a-b6c260ca238e]
name                : "eth23"

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 3c8dc910-24a1-455b-924a-b6c260ca238e
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1176922500, tx_dropped=0, tx_errors=0, tx_packets=784615}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 60cc5274-1a04-4ce2-91bb-ef669cb4baef
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
statistics          : {collisions=0, rx_bytes=24024581534, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=16026376, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 51bac33d-e4ac-4656-9700-f9da12ce0c54
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=18089315792, tx_dropped=0, tx_errors=0, tx_packets=12064077}
status              : {driver_name=igb, driver_version="3.2.10-k", firmware_version="2.10-9"}
type                : ""

_uuid               : 3496c1f9-c608-4137-beb1-ce4338945cf4
admin_state         : down
duplex              : full
ifindex             : 403
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
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 14dd55a3e3496057e7a7e0281a782b180714348d
Author:     Alex Wang &lt;ee07b291@gmail.com&gt;
AuthorDate: Fri Aug 21 15:20:24 2015 -0700
Commit:     Alex Wang &lt;ee07b291@gmail.com&gt;
CommitDate: Sat Aug 29 00:48:21 2015 +0000

    bridge: Relax the whitelist format for punix path.
    
    This commit relaxes the whitelist format for punix path of
    service controller.  Instead of only allowing
    punix:&lt;ovs_rundir&gt;/&lt;bridge_name&gt;.controller, the new format
    allows any suffix, like punix:&lt;ovs_rundir&gt;/&lt;bridge_name&gt;.*.
    &#40;except one containing '/'&#41;.
    
    Signed-off-by: Alex Wang &lt;ee07b291@gmail.com&gt;
    Acked-by: Ben Pfaff &lt;blp@nicira.com&gt;
</pre>
