---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
13bef147-e12f-4b42-ac88-1acba852708f
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
_uuid               : 4c66e0e0-afde-4c4f-acd7-1d66b8a31c52
controller          : [8fb8d788-3a69-42c2-8fbe-3376eac7390d]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [31a62fd7-8c53-4ad3-a0a6-e1f33b147b7e, 8bcf1145-f401-4c54-a6a1-4f9d1c35859c, a4b23ba9-f666-4b65-9113-f110337cfd8e]
protocols           : [OpenFlow13]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 8fb8d788-3a69-42c2-8fbe-3376eac7390d
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_connect=921, sec_since_disconnect=0, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : a4b23ba9-f666-4b65-9113-f110337cfd8e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [065f2c09-53f1-4d97-b29e-83b4ee6c3552]
name                : br0

_uuid               : 8bcf1145-f401-4c54-a6a1-4f9d1c35859c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [ad769102-8f53-446f-aa04-bc36baacdb9f]
name                : eth8

_uuid               : 31a62fd7-8c53-4ad3-a0a6-e1f33b147b7e
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [b8b6c9e6-cab0-44b1-81e7-80db36f5ca6e]
name                : eth7

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 065f2c09-53f1-4d97-b29e-83b4ee6c3552
admin_state         : down
duplex              : full
ifindex             : 958
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:4a:84:eb
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : ad769102-8f53-446f-aa04-bc36baacdb9f
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
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=7238146, tx_dropped=0, tx_errors=0, tx_packets=77153}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 

_uuid               : b8b6c9e6-cab0-44b1-81e7-80db36f5ca6e
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
statistics          : {collisions=0, rx_bytes=3075175231, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=72756142, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=3.10-0}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 50c1efc9003fe5b0bcaf548b2c01735247d820d4
Author:     Joe Stringer &lt;joestringer@nicira.com&gt;
AuthorDate: Thu Apr 10 16:56:12 2014 +1200
Commit:     YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
CommitDate: Thu Apr 10 14:54:36 2014 +0900

    ofproto-dpif.at: Update MPLS test names.
    
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
    Signed-off-by: YAMAMOTO Takashi &lt;yamamoto@valinux.co.jp&gt;
</pre>
